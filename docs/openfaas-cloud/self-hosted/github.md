## Configure GitHub for OpenFaaS Cloud

This guide is for connecting your self-hosted OpenFaaS Cloud to GitHub.

We will cover creating and configuring a GitHub App for webhooks and events and then a GitHub OAuth app for logging in to OpenFaaS Cloud with your GitHub Account.

### Create a GitHub App

* Click on *Profile* -> *Settings* -> *Developer Settings*

* Click *GitHub Apps* and *New GitHub App*

* Enter your details

    Fill out "GitHub App Name", "Webhook URL" and leave the secret blank for now.

    Example webhook URL: `https://system.YOURDOMAIN.TLD/github-event`

    ![Create your App](/images/openfaas-cloud/github-app-01.png)

* Set the Permissions as follows

    Checks: Read & Write

    Commit Statuses: Read & Write

    Repository contents: Read-only

    ![Set-up your permissions](/images/openfaas-cloud/github-app-02.png)

* No User permissions are required

* Update "Subscribe to events" and select "Push" and "Repository"

    ![](/images/openfaas-cloud/github-app-03.png)

* Set the app to be installed on your account

    ![](/images/openfaas-cloud/github-app-04.png)

* Finally click *Create GitHub App*

* Navigate to your App's page on GitHub

* Click "Generate a private key". A file will be downloaded, rename it to `private-key.pem` and place it in `~/Downloads`.

* Note down your App's ID from this page

* Take a note of the URL for your "Public Page", you will need to share this with your users

* Install your App

  Click *Install App*, then navigate to one of your GitHub repos or organisations and install the App onto selected repositories.

* Diagostics

    At any point you can return to this page and click "Advanced" here you can expand the requests and responses of all webhooks generated by your App.

If you are enabling auth/oauth then skip to the next section.

That's it, you can now input this data into the [ofc-bootstrap](https://github.com/openfaas-incubator/ofc-bootstrap) 1-click tool, or follow the developer instructions in the [openfaas-cloud](https://github.com/openfaas/openfaas-cloud/tree/master/docs) repo.

### Create a GitHub OAuth integration (optional)

We will now create a GitHub OAuth integration so that we and our users can log into OpenFaaS Cloud using our GitHub account.

* Click on *Profile* -> *Settings* -> *Developer Settings*

* Click *OAuth Apps* and *New OAuth App*

* Fill out the form

    ![](/images/openfaas-cloud/github-oauth-01.png)

    Set the Application Name as `Login to My OpenFaaS Cloud`

    Set the Homepage URL to `https://www.openfaas.com/`

    Set your Authorization URL to `https://auth.system.domain.tld/` where domain.tld is the domain name you are using for OpenFaaS Cloud

* Click *Register Application*

* Collect your `client_id` and `client_secret`

    ![](/images/openfaas-cloud/github-oauth-02.png)

That's it, you can now input this data into the [ofc-bootstrap](https://github.com/openfaas-incubator/ofc-bootstrap) 1-click tool, or follow the developer instructions in the [openfaas-cloud](https://github.com/openfaas/openfaas-cloud/tree/master/docs) repo.