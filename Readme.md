# Terraform GitHub Actions Workflow

This repository contains a **test workflow** designed to automate Terraform functions whenever code is pushed to the repository. The workflow runs on **GitHub Actions** and ensures that Terraform infrastructure is initialized, formatted, planned, applied, and later destroyed automatically.

## **Workflow Overview**
This workflow is triggered when code is pushed to the repository. It performs the following Terraform actions:

1. **Checkout Repository** - Fetches the latest code.
2. **Configure AWS Credentials** - Authenticates with AWS using secrets stored in GitHub.
3. **Initialize Terraform** - Runs `terraform init` to set up the Terraform working directory.
4. **Format Terraform Code** - Runs `terraform fmt` to ensure proper formatting.
5. **Plan Deployment** - Runs `terraform plan` to preview infrastructure changes.
6. **Apply Changes** - Runs `terraform apply -auto-approve` to deploy infrastructure.
7. **Wait 5 Minutes** - Pauses execution before destroying resources.
8. **Destroy Infrastructure** - Runs `terraform destroy -auto-approve` to remove infrastructure.

## **Getting Started**
To use this workflow, follow these steps:

1. **Fork this repository** or clone it locally.
2. **Ensure you have Terraform installed** if running locally.
3. **Add AWS credentials** as GitHub Secrets:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - (Optional) `AWS_REGION`
4. **Modify Terraform files (`.tf` files) as needed.**
5. **Push changes to the repository**, and the workflow will trigger automatically.

## **GitHub Secrets Used**
The workflow requires AWS credentials to deploy infrastructure. These secrets should be stored in the **GitHub repository settings** under **Secrets and Variables** → **Actions**.

| Secret Name            | Description |
|------------------------|-------------|
| `AWS_ACCESS_KEY_ID`    | AWS access key for authentication |
| `AWS_SECRET_ACCESS_KEY` | AWS secret key for authentication |
| `AWS_REGION`           | (Optional) AWS region for deployment |

## **Modifying the Workflow**
If you need to adjust the workflow, edit the **`.github/workflows/terraform-automate.yml`** file.

### Example Modifications:
- Change the **Terraform commands** (e.g., remove auto-approve for manual review).
- Add a **notification step** to Slack or email.
- Modify the **AWS region** if deploying to a different location.

## **Troubleshooting**
If the workflow does not trigger or fails:
- Ensure **Terraform files** are correctly formatted (`terraform fmt`).
- Check if **AWS credentials** are correctly added in GitHub Secrets.
- Review the **GitHub Actions logs** for detailed error messages.
