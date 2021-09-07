# Configure the tool

The following guide shows the steps to configure several popular LMS to work with the Microsoft Learn LTI application. If your LMS is not listed here, consult your LMS vendor on how to configure LTI application. Regardless of the LMS, the typical workflow should remain the same:

1. Obtain parameters from the deployed Microsoft Learn LTI application’s registration page
2. Configure an LTI tool on the LMS using the parameters from step 1.
3. Obtain parameters from the configured LTI tool.
4. Configure the Microsoft Learn LTI application using the parameters from step 3.

By now, you should've obtained the following parameters from the Microsoft Learn LTI application’s registration page. If not, follow the deployment guide to deploy Microsoft Learn LTI application and obtain the following parameters from the registration page.

- Login URL
- Launch URL
- Domain URL
- Public Key
- Public JWK
- Public JWK Set URL

If you are not the one who deployed the application, you need to obtain the parameters from that person.

The configuration steps slightly differ depending on the LMS you are using. In general, they will involve registering the Microsoft Learn LTI application as an external tool in the LMS and registering the parameters of external tool back in the Microsoft Learn LTI application's registration page. The following examples show how to configure Microsoft Learn LTI application with three of the popular LMS.

- [Open edX](#Open-edX-LMS)


## Open edX LMS

The following steps show how to configure an LTI tool on a Open edX LMS.

### lTI 1.3

1. Sign into Open edX Studio (I.e., the Content Management System of Open edX) with the admin account.
2. Enable the LTI Consumer XBlock in Open edX Studio through the advanced settings based on the following steps:
   1. From the main page of a specific course, navigate to **Settings -> Advanced Settings** from the top menu.
   2.	Check for the **advanced_modules** policy key and add **"lti_consumer"** to the policy value list, per the below figure.
   ![Config_edx.2](/images/Config_edx.2.png)
   3.	Click the **"Save changes"** button.
3. Edit the unit in which you want to add the remote LTI tool and select **Advanced** from within the **Add New Component** section. Select **LTI Consumer**.
4. In the CMS Admin panel, enable course edit lti fields. To enable Course edit lti fields, select "Course edit lti fields enabled flags" under XBLOCK CONFIGURATION section and then enable it. **Course id can be found in course overviews.**
![Config_edx.5](/images/Config_edx.5.png)
5. In the LMS Admin panel, enable the transfer of PII (incl. email) between an edX LTI Xblock component and the MS Learn Functions App.
   1. Add a course waffle flag from http://EDX-LMS-URL/admin/waffle_utils/waffleflagcourseoverridemodel/.
   2. Set waffle flag to - lti_consumer.lti_nrps_transmit_pii and set course key to your course key. : YOUR-COURSE-ID.
   3. Make sure to set the override choice option to - Force On
   ![Config_edx.1](/images/Config_edx.1.png)
   4. (optional) For security reasons, edX only allows to transmit enrolment PII for courses with less than 1000 students per default. To change this set the LTI_NRPS_ACTIVE_ENROLLMENT_LIMIT Django setting to a lower/higher value.
   --> adapted from - https://github.com/edx/xblock-lti-consumer/pull/124
6. Select **Edit** inside the newly created component.
![Config_edx.7](/images/Config_edx.7.png)
7. In the **LTI Version** field, select **LTI 1.3**.
8. Enter the LTI 1.3 settings provided in the Learn Lti Registration form. For basic LTI 1.3 tools, you need to set the following settings:
   * **LTI 1.3 Tool Launch URL** (can also be called redirect url)
   * **LTI 1.3 OIDC URL** (can also be called login url)
   * **LTI 1.3 Tool Public Key** (a key provided by the LTI tool) The key will look similar to this example:
   -----BEGIN PUBLIC KEY-----abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345 abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345abcde12345-----END PUBLIC KEY-----
   You should paste the key from the tool directly into the configuration field. For more information about each setting, see the LTI Component Settings.
9. Enable LTI NRPS through setting it to True. 
![Config_edx.3](/images/Config_edx.3.png)
10. Enable Request user's username and email settings to True.
![Config_edx.6](/images/Config_edx.6.png)
11. Select **Save**.
12. The Studio page will refresh and display LTI configuration required by the tool. Copy each of those values and follow the instructions provided by the tool to set them up.
   * **Client** -> Client ID
   * **Keyset URL** -> JWK Set URL
   * **OAuth Token URL** ->Access Token URL
   * **OIDC Callback URL** -> Authorizaton URL
   ![Config_edx.4](/images/Config_edx.4.png)
13. Publish the unit where the LTI Component is located.


You're all set. The Learn LTI tool is now configured on your Blackboard Learn LMS and your Educators will be able to use it to bring Microsoft Learn content to their courses. Follow the educator guide to create assignments that use the Learn LTI tool.
