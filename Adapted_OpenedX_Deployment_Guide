# Open edX Deployment Instructions 

## Table of Contents
1. Clone the repo: [link](#clone-the-repo)
2. Deploy to Azure Subscription using the script: [link](#deploy-to-azure-subscription-using-the-script)
3. Configure the tool: [link](#configure-the-tool)

## Prerequisites
To begin, you will need:
- Open edX 
You can install Open edX either through [Tutor](https://docs.tutor.overhang.io/quickstart.html) after creating a virtual machine on your azure or using our [Open edX Azure quick-start template](https://github.com/Azure/azure-quickstart-templates/tree/master/application-workloads/opendx/openedx-tutor-lilac-ubuntu)  

## Follow these steps to adapt your Open edX:

1. Add codes shown in the picture below to the view.py file of xblock-lti-consumer that it can "guess" and fill in the given_name and family_name of the user by splitting the comma (",") or space (" ") in the user's full_name. No need to split the full name necessarily if there has no comma or space in the full name because Learn LTI only needs given name and can have family name blank ("").
![xblock-lti-consumer-codes](/images/xblock-lti-consumer-codes.png)

2. Update the xblock-lti-consumer in Open edX using following commands:
      1. tutor local quickstart
      2. nano $(tutor config printroot)/env/build/openedx/Dockerfile
      3. Edit the Dockerfile in 2 locations
          1)	at EDX_PLATFORM_REPOSITORY, change the edx/edx-platform to YankeZhang/edx-platform to pull our forked github code
          2)	right below it, set the version to open-release/ltiopenedx.9
      4. tutor images build openedx
      5. tutor local stop
      6. tutor local quickstart

Now, your Open edX has been updated to the our adapted Open edX. 
