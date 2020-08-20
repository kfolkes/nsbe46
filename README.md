# NSBE 46 💻 | Azure Web Apps for Linux 📦💙 

### Repository Contents 

| Files             |  Content                                   |
|----------------------|--------------------------------------------|
| `application.py`         | python Flask App         |
| `requirements.txt`       | File containing a list of items to be installed using pip install|


# Set up your Azure Account 
Have an Azure account with an active subscription.

* Azure for Students | $100 in Azure for 12 months with free tier of services - no credit card required with academic verification
* Azure for Students Starter | use select Azure products like App Services for free - no credit card required with academic verification
* Azure Free Account | $200 in Azure for one month with free tier of services - requires a credit card and probably the best fit for faculty evaluating Azure for course instruction unless your organization has a grant or enterprise agreement.

# Install Python 3.6 or Higher

Install [Python 3.6 or higher](https://www.python.org/downloads/).

# Install Azure CLI 2.0.80 

Install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) 2.0.80 or higher, with which you run commands in any shell to provision and configure Azure resources.


# Now we rolling ... 

Open a terminal/cmd window and check your Python version is 3.6 or higher:

```
py -3 --version
```

Check that your Azure CLI version is 2.0.80 or higher:

```
az --version
```

Then sign in to Azure through the CLI:

```
az login
```

This command opens a browser to gather your credentials. When the command finishes, it shows JSON output containing information about your subscriptions.

Once signed in, you can run Azure commands with the Azure CLI to work with resources in your subscription.

# Clone this sample 

```
git clone https://github.com/kfolkes/nsbe46
```
Then go into that folder:

```
cd nsbe46
```

The sample code contains an application.py file, which tells App Service that the code contains a Flask app.


# Let's get "thangz" running (locally)

First create a virtual environment and install dependencies:
```
py -3 -m venv env
env\scripts\activate
pip install -r requirements.txt
```

Then set the FLASK_APP environment variable to the app's entry module and run the Flask development server:
```
SET FLASK_APP=application.py
flask run

```

Open a web browser, and go to the sample app at http://localhost:5000/. The app displays the message Hello World!.

In your terminal window, press Ctrl+C to exit the Flask development server.

# Now it's time to deploy 
```
az webapp up --sku F1 -n <app-name>

```
- If the az command is not recognized, be sure you have the Azure CLI installed as described in Set up your initial environment.
- Replace <app_name> with a name that's unique across all of Azure (valid characters are a-z, 0-9, and -). A good pattern is to use a combination of your company name and an app identifier.
- The --sku F1 argument creates the web app on the Free pricing tier. Omit this argument to use a faster premium tier, which incurs an hourly cost.
- You can optionally include the argument -l <location-name> where <location_name> is an Azure region such as centralus, eastasia, westeurope, koreasouth, brazilsouth, centralindia, and so on. You can retrieve a list of allowable regions for your Azure account by running the az account list-locations command.
  
  
  The command may take a few minutes to complete. While running, it provides messages about creating the resource group, the App Service plan and hosting app, configuring logging, then performing ZIP deployment. It then gives the message, "You can launch the app at http://<app-name>.azurewebsites.net", which is the app's URL on Azure.
  
![CMD](/images/deployaz.png)


# Browse to the app
Browse to the deployed application in your web browser at the URL http://<app-name>.azurewebsites.net.
The Python sample code is running a Linux container in App Service using a built-in image.

![depolyedApp](/images/success_az.png)
# Python Flask sample for Azure App Service (Linux)

This is a minimal sample app that demonstrates how to run a Python Flask application on Azure App Service on Linux.

For more information, please see the [Python on App Service quickstart](https://docs.microsoft.com/azure/app-service/containers/quickstart-python).

Congratulations! You've deployed your first Python app to App Service. You So Smart!

# Redeploying updates

In your favorite code editor, open application.py and update the hello function as follows. This change adds a print statement to generate logging output that you work with in the next sectioni or you can change it to whatever you want. 


```
def hello():
    print("Handling request to home page.")
    return "Wha Gwan NSBE!"

```
Save your changes and exit the editor.

Redeploy the app using the az webapp up command again:

```
az webapp up

```

This command uses values that are cached locally in the .azure/config file, including the app name, resource group, and App Service plan.



## Notes and References 
 - Flask: https://flask.palletsprojects.com/en/1.1.x/quickstart/
 - Python Configurations: https://docs.microsoft.com/en-us/azure/app-service/configure-language-python
 
 
## Instructor Information 
Krystal Folkes - Azure Support Technical Advisor,
Team: Azure App Service, Open Source Software OSS
Email: Krystal.folkes@microsoft.com 

 
