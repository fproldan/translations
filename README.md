## Translations

Example app to illustrate the usage of the docs translation action


### Google Translation API Setup

To obtain the credentials JSON file for using the Google Cloud Translation API, you'll need to create a service account and generate a key file associated with that account. Here's a step-by-step guide on how to do it:

**1. Go to the Google Cloud Console:**

Visit the [Google Cloud Console](https://chatgpt.com/c/768c08ec-9330-4b0a-9c55-5e0119f695af#:~:text=Console%3A%0AVisit%20the-,Google%20Cloud%20Console,-.).

**2. Create a new project (if you haven't already):**

Click on the project dropdown at the top of the page and select "New Project". Follow the prompts to create a new project.

**3. Enable the Cloud Translation API:**

Once your project is created, navigate to the "APIs & Services" > "Library" page in the Cloud Console. Search for "Cloud Translation API" and enable it for your project.

**4. Create a service account:**

Go to the "APIs & Services" > "Credentials" page. Click on "Create credentials" and select "Service account". Fill in the required fields and click "Create".

**5. Assign permissions to the service account:**

After creating the service account, you'll be prompted to grant it access to certain resources. Assign the "Cloud Translation API User" role to the service account.

**6. Generate a key file:**

Once the service account is created, click on it from the "Credentials" page. Then, click on "Add key" > "Create new key". Choose the JSON key type and click "Create". This will download a JSON file containing your credentials.

**7. Download the JSON key file:**

Save the downloaded JSON key file securely to your computer. This file contains your credentials and should be kept confidential.


### Repository Configuration

**1. Set `GOOGLE_APPLICATION_CREDENTIALS` environment variable:**

- Go to Settings > Secrets and variables > Actions > **New repository settings**
    - Name: `GOOGLE_APPLICATION_CREDENTIALS`
    - Value: the content of the JSON credentials file

**2. Configuration for Actions:**

- Go to Settings >  Actions > General > Workflow permissions and enable the following:
    - Read and write permission.    
    - Allow GitHub Actions to create and approve pull requests.


### Usage

Every Pull Request that makes changes in any .md file under `docs/*/en/` will trigger the action.
The action will make a Pull Request with the translated files for every language configured in `docs_languages` in hooks under `docs/*/{LANGUAGE}/`, if the folder for the language doesn't exists it will be created.


`docs_languages` should be a list of languages i.e:

`docs_languages = ['es', 'fr']`





#### License

MIT