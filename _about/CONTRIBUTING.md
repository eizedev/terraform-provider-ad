# Building and installing

In order to contribute to the provider, you have to build and install it manually as indicated below. Make sure you have a supported version of Go installed and working. Check out or download this repository, then open a terminal and change to its directory.

## Preparation

Examples for Ubuntu Linux.

### Golang, Make

```shell
sudo apt install golang-go
sudo apt install make
```

### Fixing source code (if needed)

```shell
make fmt
```

### Terraform

```shell
# Add gpg key to keyring
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmour -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
# Check key
gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
# Add official Hashicorp repository
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
# update
sudo apt update
# install terraform
sudo apt install terraform
```

## Installing the provider to `terraform.d/plugins`

```shell
make build
go install
```

This will build the provider and place the provider binary in the top level of your provider directory.

You will then have to create a symlink in your[plugins directory](https://www.terraform.io/docs/extend/how-terraform-works.html#plugin-locations) in order for Terraform to detect your provider when you run `terraform init`. Note that the plugin path is different between Terraform versions 0.12 and 0.13.

You are now ready to use the provider. You can find example configurations to test with in this repository under the `./examples` folder.

## Using `-plugin-dir`

Alternatively, you can run:

```shell
make build
```

This will place the provider binary in the top level of the provider directory. You can then use it with terraform by specifying the `-plugin-dir` option when running `terraform init`

```shell
terraform init -plugin-dir /path/to/terraform-provider-ad
```
