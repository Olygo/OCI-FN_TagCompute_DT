# OCI-FN_TagCompute_DT

**OCI-FN_TagCompute_DT** is an OCI Function demonstrating how to automatically apply Defined_Tags using a custom variable (here instance display_name) to compute resources (instance, boot and block volumes)
In this scenario I can now identify all the cost related to a single instance, and I can use OCI Cost Analysis to filter accordingly

![Script Output](https://objectstorage.eu-frankfurt-1.oraclecloud.com/p/ArOLIb0vUtXvhlffPSXKqA1V7pkm4l_Ecrj7pqEXWJ6tL-BSGg41CWqsIEeUMOa9/n/olygo/b/git_images/o/OCI-FN_TagCompute_DT/CostAnalysis.png)

# Features 
- **OCI-FN_TagCompute_DT** :
	- when OCI Events send **Instance - Launch End** notification:
		- function tags instance + boot volume 
	- when OCI Events send **Volume - Attach End** notification:
		- function tags block volumes

- No need to tag boot/block volumes backups, they automatically get same tags as their parent boot/block volumes

# Prerequisites 
- Edit **func.py** variables to use your own tags
> 	- TagNamespace = 'MyTags'
> 	- TagKey = 'display_name'
	
- Create a tag namespace and key:

	[https://docs.oracle.com/en-us/iaas/Content/Tagging/Tasks/managingtagsandtagnamespaces_topic-To_create_a_tag_namespace.htm](https://docs.oracle.com/en-us/iaas/Content/Tagging/Tasks/managingtagsandtagnamespaces_topic-To_create_a_tag_namespace.htm) 

![Script Output](https://objectstorage.eu-frankfurt-1.oraclecloud.com/p/ArOLIb0vUtXvhlffPSXKqA1V7pkm4l_Ecrj7pqEXWJ6tL-BSGg41CWqsIEeUMOa9/n/olygo/b/git_images/o/OCI-FN_TagCompute_DT/TagNamespace.png)

- Create an OCI Event monitoring

	[https://docs.oracle.com/en-us/iaas/Content/Events/Task/managingrules.htm](https://docs.oracle.com/en-us/iaas/Content/Events/Task/managingrules.htm) 

**/!\ The Event Rule must be created in your Root Compartment if you want to monitor your whole tenancy**

![Script Output](https://objectstorage.eu-frankfurt-1.oraclecloud.com/p/ArOLIb0vUtXvhlffPSXKqA1V7pkm4l_Ecrj7pqEXWJ6tL-BSGg41CWqsIEeUMOa9/n/olygo/b/git_images/o/OCI-FN_TagCompute_DT/Events.png)

- **After** the function has been deployed add an action to your event to launch your OCI function:

![Script Output](https://objectstorage.eu-frankfurt-1.oraclecloud.com/p/ArOLIb0vUtXvhlffPSXKqA1V7pkm4l_Ecrj7pqEXWJ6tL-BSGg41CWqsIEeUMOa9/n/olygo/b/git_images/o/OCI-FN_TagCompute_DT/Event_Action.png)


# Quick set up guide 

Download the step by step guide to quickly set up your environment and deploy your function to OCI:
[https://github.com/Olygo/OCI-FN_TagCompute_DT/raw/main/OCI_Function_QuickStart.pdf](https://github.com/Olygo/OCI-FN_TagCompute_DT/raw/main/OCI_Function_QuickStart.pdf)

## Questions ?
**_olygo.git@gmail.com_**


## Disclaimer
**Please test properly on test resources, before using it on production resources to prevent unwanted outages or unwanted bills.**
