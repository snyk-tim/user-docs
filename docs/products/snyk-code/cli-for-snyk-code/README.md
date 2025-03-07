# Using Snyk Code via Snyk CLI

{% hint style="info" %}
Make sure Snyk Code is enabled for your organization, see [Getting started with Snyk Code](../../../getting-started/getting-started-snyk-products/getting-started-with-snyk-code.md#stage-1-enable-snyk-code) for details.
{% endhint %}

The Snyk Command Line Interface ([CLI](../../../features/snyk-cli/)) for Snyk Code helps you find and fix security flaws in your code on your local machine.

## **Install the Snyk CLI**

To install the Snyk CLI, you can use any of the following:

* npm: `npm install -g snyk`
* Homebrew: `brew tap snyk/tap && brew install snyk`
* Scoop: `scoop bucket add snyk <https://github.com/snyk/scoop-snyk>`
* [**A manual installer**](https://github.com/snyk/snyk/releases) available from GitHub

For more detailed installation guidance and options, see [Install the Snyk CLI](../../../features/snyk-cli/install-the-snyk-cli/).

## **Authentication**

After the installation, authenticate with Snyk to test your image, running snyk auth from the CLI:

```
snyk auth
```

For more details about authentication, see [Authenticate the CLI with your account](../../../features/snyk-cli/install-the-snyk-cli/authenticate-the-cli-with-your-account.md)

## **Testing a project or folder**

To test the current folder, run `snyk code test` with no parameters.

To test another context, run `snyk code test <my-folder-path>` with a path to a file or folder as the parameter.

All sub-folders inside the provided folder are also scanned.

### "Not supported" message

{% hint style="danger" %}
**Snyk Code is not supported for org** _**your.org**_

A minimum version of `1.716.0` is required to use CLI for Snyk Code.
{% endhint %}
