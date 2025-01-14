<a href="https://terraform.io">
    <img src="https://github.com/hashicorp/terraform-provider-azurerm/raw/main/.github/tf.png" alt="Terraform logo" title="Terraform" align="left" height="50" />
</a>

# Terraform Provider for Windows Active Directory (AD)

![Status: Tech Preview](https://img.shields.io/badge/status-experimental-EAAA32) [![Releases](https://img.shields.io/github/release/hashicorp/terraform-provider-ad.svg)](https://github.com/hashicorp/terraform-provider-ad/releases)
[![LICENSE](https://img.shields.io/github/license/hashicorp/terraform-provider-ad.svg)](https://github.com/hashicorp/terraform-provider-ad/blob/main/LICENSE)
![Unit tests](https://github.com/hashicorp/terraform-provider-ad/workflows/Unit%20tests/badge.svg)

This Windows AD provider for Terraform allows you to manage users, groups and group policies in your AD installation.

This provider is a technical preview, which means it's a community supported project. It still requires extensive testing and polishing to mature into a HashiCorp officially supported project. Please [file issues](https://github.com/hashicorp/terraform-provider-ad/issues/new/choose) generously and detail your experience while using the provider. We welcome your feedback.

By using the software in this repository (the AD provider), you acknowledge that:

* The AD provider is still in development, may change, and has not been released as a commercial product by HashiCorp and is not currently supported in any way by HashiCorp.
* The AD provider is provided on an "as-is" basis, and may include bugs, errors, or other issues.
* The AD provider is NOT INTENDED FOR PRODUCTION USE, use of the Software may result in unexpected results, loss of data, or other unexpected results, and HashiCorp disclaims any and all liability resulting from use of the AD provider.
* HashiCorp reserves all rights to make all decisions about the features, functionality and commercial release (or non-release) of the AD provider, at any time and without any obligation or liability whatsoever.

## Changes to original project

Credits to the following comment in issue: [Looking for community feedback on the AD provider](https://github.com/hashicorp/terraform-provider-ad/issues/53#issuecomment-1941310970)

* Clone original repo

```shell
git clone https://github.com/hashicorp/terraform-provider-ad.git
cd terraform-provider-ad/
```

* Pull "must have" patches (I want to thanks users who created these patches 👍)

```shell
git remote add bmhughes https://github.com/bmhughes/terraform-provider-ad.git
git pull bmhughes ad-user-name
git pull bmhughes fix-user-password-never-expires

git remote add hanneshayashi https://github.com/hanneshayashi/terraform-provider-ad.git
git pull hanneshayashi additional-group-attributes

git remote add shubhambjadhavar https://github.com/shubhambjadhavar/terraform-provider-ad.git
git pull shubhambjadhavar main

git remote add randomswdev https://github.com/randomswdev/terraform-provider-ad.git
git pull randomswdev main
```

* Perhaps you need to fix some merge conflicts, f.e. for `index.md` after pulling changes from one forked repository (done in my project)
* Build provider as described [here](https://github.com/hashicorp/terraform-provider-ad/blob/main/_about/CONTRIBUTING.md)
* Please note that there can be other issues which isn't reported here or fixed using patches above, so **use your newly built provider at your own risk**

Patches above solved the most of the issues that I have faced during tests but now I found another one - using commas in OU name will lead to the issue with it's distinguishedName due to the escaping backslash in state file after creating OU.

## Requirements

* [Terraform](https://www.terraform.io/downloads.html) version 0.12.x+
* [Windows Server](https://www.microsoft.com/en-us/windows-server) 2012R2 or greater 
* [Go](https://golang.org/doc/install) version 1.16.x+

## Getting Started

If this is your first time here, you can get an overview of the provider by reading our [introductory blog post](https://www.hashicorp.com/blog/manage-active-directory-objects-new-windows-ad-provider-hashicorp-terraform). Otherwise, start by downloading a copy of our latest build from the [registry](https://registry.terraform.io/providers/hashicorp/ad/latest).

Once you have the plugin installed, review the [docs](docs/) folder to understand which configuration options are available. You can find examples and more in [our examples folder](examples/). Don't forget to run `terraform init` in your Terraform configuration directory to allow Terraform to detect the provider plugin.

## Contributing

We welcome your contribution. Please understand that the experimental nature of this repository means that contributing code may be a bit of a moving target. If you have an idea for an enhancement or bug fix, and want to take on the work yourself, please first [create an issue](https://github.com/hashicorp/terraform-provider-ad/issues/new/choose) so that we can discuss the implementation with you before you proceed with the work.

You can review our [contribution guide](_about/CONTRIBUTING.md) to begin. You can also check out our [frequently asked questions](_about/FAQ.md).
