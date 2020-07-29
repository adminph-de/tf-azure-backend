[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/adminph-de/tf-azure-backend">
    <img src="/images/logo.png" alt="Terraform & Azure">
  </a>
  <h3 align="center">Deploy a Remote Backend to Azure with Terraform</h3>
</p>

<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
* [Deployment](#deployment)
* [Contact](#contact)
* [Referenzes](#referenzes)

## About The Project

Using Terraform to deploy a StorageAccount in Azure to use it as a [Terraform Remote Backend](https://www.terraform.io/docs/backends/types/remote.html) to store your future tfstate files. Part of the reposotory is a folder called ```.devcontainer``` it contains the Docker container configuration to use it with [Microsoft Visial Studio Code](https://code.visualstudio.com/download) and the [Remote-Container](https://code.visualstudio.com/docs/remote/containers) technologie. [Terraform](https://www.terraform.io/downloads.html) and [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) is installed, if you run the container. You need apart of [Microsoft Visial Studio Code](https://code.visualstudio.com/download) [Docker Desktop](https://www.docker.com/get-started) installed on your PC, MAC or Linux to use [Remote-Container](https://code.visualstudio.com/docs/remote/containers). This is only optional and not requited to run the Terraform scripts.


### Deployment
 
1. Clone the repo
```sh
git clone https://github.com/adminph-de/tf-azure-backend.git
```
2. Azure Credential file:
Create an addinal file in your cloned repo, called: ```azurecert.conf``` with your spezific ```TENANT_ID```, ```SUBSCRIPTION_ID``` and a ```Azure Service Principal (SPN)``` ```CLIENT_ID``` and ```CLIENT_SECRET``` variable. Find the HowToBuild a SPN in the referenzes below.

Content of the file:
```sh
ARM_TENANT_ID="0000000-0000-0000-0000-000000000000"
ARM_SUBSCRIPTION_ID="0000000-0000-0000-0000-000000000000"
ARM_CLIENT_ID="0000000-0000-0000-0000-000000000000"
ARM_CLIENT_SECRET="0000000-0000-0000-0000-000000000000"
```

3. Terraform Variables file: 
Create a ```terraform.tfvars``` file in your cloned repo with the variable values like this:
```sh
project     = "Remote Backend for tfstate files"
environment = "PROD"
location    = "westus2"
```

4. Run Terraform Init:
```bash
terraform init -backend-config=azurecreds.conf
```

5. Run Terraform Plan:
```sh
terraform plan
```

6. Run Terraform Apply:
```
terraform apply -auto-approve
```

7. Check your result in your Azure Subscription

<!-- CONTACT -->
## Contact

[LinkedIN](https://www.linkedin.com/in/patrickhayo/?locale=en_US) - [Twitter](https://twitter.com/N00ky2010) - [Email](patrick.hayo@flsmidth.com)

Project Link: [https://github.com/adminph-de/tf-azure-backend](https://github.com/adminph-de/tf-azure-backend)

<!-- REFERENZES -->
## Referenzes

Author of the scrpit source is [Guillermo Musumeci](https://medium.com/@gmusumeci). Find detaild docmentation and explainations in his article:
* [How to Create an Azure Remote Backend for Terraform](https://medium.com/@gmusumeci/how-to-create-an-azure-remote-backend-for-terraform-67cce5da1520)

Addinaly to this article, check:
* [How to manage Terraform state in Azure Blob Storage](https://medium.com/developingnodes/how-to-manage-terraform-state-in-azure-blob-storage-870a80917450)
* [Terraform CLI (azurerm)](https://www.terraform.io/docs/backends/types/azurerm.html)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/adminph-de/tf-azure-backend.svg?style=flat-square
[contributors-url]: https://github.com/adminph-de/tf-azure-backend/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/adminph-de/tf-azure-backend.svg?style=flat-square
[forks-url]: https://github.com/adminph-de/tf-azure-backend/network/members
[stars-shield]: https://img.shields.io/github/stars/adminph-de/tf-azure-backend?style=flat-square
[stars-url]: https://github.com/adminph-de/tf-azure-backend/stargazers
[issues-shield]: https://img.shields.io/github/issues/adminph-de/tf-azure-backend.svg?style=flat-square
[issues-url]: https://github.com/adminph-de/tf-azure-backend/issues
[license-shield]: https://img.shields.io/github/license/adminph-de/tf-azure-backend.svg?style=flat-square
[license-url]: https://github.com/adminph-de/tf-azure-backend/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/patrickhayo/?locale=en_US
[product-screenshot]: images/screenshot.png
