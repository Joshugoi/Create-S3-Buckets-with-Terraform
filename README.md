<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-terraform1)

**Author:** Joshua Banh  
**Email:** banhjosh@gmail.com

---

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

This project demonstrates the automation of Amazon S3 bucket deployment using Terraform. I will cover the setup and installation of Terraform, configuring AWS credentials in the terminal, writing Terraform configuration to create and manage an S3 bucket, and automating file uploads to that bucket.

### Tools and concepts

The core AWS Services utilized in this project were Amazon S3 (Simple Storage Service) for object storage and IAM (Identity and Access Management) for secure access and credential management. The key technical concept demonstrated was Infrastructure as Code (IaC), implemented specifically using the automation tool Terraform."

### Project reflection

This project was completed in approximately one hour. The most challenging aspect was navigating the extensive Terraform documentation and configuration options, specifically in understanding the optimal ways to rapidly provision the infrastructure. The most rewarding outcome, however, was gaining a practical understanding of Terraform's efficiency and power, which clearly illustrated why employers highly value candidates with strong proficiency in Infrastructure as Code (IaC) tools.

My motivation for undertaking this project today was to gain practical insight into Terraform's widespread adoption and its value within the cloud industry. To further enhance the learning experience with NextWork, I suggest integrating more complex, hands-on projects that require deeper architectural design and troubleshooting, thereby allowing users to achieve true proficiency.

---

## Introducing Terraform

Terraform is a tool that helps you build and manage your cloud infrastructure using code.

Instead of setting up resources manually in the AWS console or CLI, you write a script that tells Terraform exactly what you want in your cloud infrastructure, like servers, databases, and networks. Terraform then automatically builds all of this for you, using your script as a blueprint.

Infrastructure as Code (IaC) is the practice of describing your cloud setup (like your servers, storage, networks) in plain text files instead of clicking through a web console. When you run those files, the cloud builds everything exactly as you've written it written. Because the description lives in code, you can version-control it, share it with teammates, and recreate the same environment any time you need.

Terraform uses configuration files to define and manage infrastrucure, main.tf is the central file that'll allow you to strucure your infrstrucure.

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in blocks. The advantage of doing this is that by keeping each piece of your infrastructure in its own block, the file stays easy to read and I can tweak one part without touching the rest of my setup



### My main.tf configuration has three blocks

The first block indicates what cloud provider i am using, in my main.tf is aws in us-east-1. The second block provisions what resource i am using, so in this case i amd using amazon S3 bucket. The third block manages the permissions to access the s3 bucket.

<img width="1512" height="982" alt="Screenshot 2025-10-26 at 7 53 12 PM" src="https://github.com/user-attachments/assets/4b66f92b-a200-4d71-bac8-90afe454278d" />


---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to create and manage AWS S3 buckets. The documentation shows different configurations of how to set up your AWS S3 bucket and how they interact with other services.

I customized the S3 bucket configuration by adding a resource tag. This practice ensures proper asset governance and simplifies resource identification and filtering when querying cloud assets. I will confirm the successful application of this customization by running the Terraform configuration file and inspecting the resulting bucket attributes.

<img width="1000" height="1000" alt="Screenshot 2025-10-26 at 7 48 25 PM" src="https://github.com/user-attachments/assets/617e72ab-073a-478d-b483-25860e229a9c" />

---

## Terraform commands

I ran 'terraform init' to download the necessary plugins, setting up the backend, preparing modules and creating a lock file to track version of everythin teraaform is using, ensuring that everyone is on the same page.

Next, I ran 'terraform plan' to execute my plan, which shows what changes are happening within my infrastrucure based on my configuration file. 

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

When I tried to plan my Terraform configuration, I received an error message that says "Error: No valid credential sources found" because Terraform does not have access to my AWS Account to create my infrsstrucure.

To resolve the deployment error, the initial corrective action was the installation of the AWS Command Line Interface (CLI). The AWS CLI is a prerequisite, as it enables direct management and interaction with all AWS services from the terminal environment.

To enable Infrastructure as Code (IaC) management, I provisioned AWS Access Keys (Access Key ID and Secret Access Key) and configured them within Terraform. This action grants Terraform the necessary programmatic credentials to authenticate with and provision resources in my AWS administrator account.

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

I executed the terraform apply command to implement the defined infrastructure changes. This command validates the execution plan and provisions the Amazon S3 bucket resource in my AWS account, thereby enforcing the desired state declared in the configuration files.

The sequential execution of terraform init, plan, and apply is a crucial best practice in Infrastructure as Code (IaC). This workflow ensures that configuration syntax is valid and, most importantly, provides a preview of intended infrastructure changes before they are committed, allowing for the early detection and mitigation of errors.

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to add a image to my s3 bucket. bucket = aws_s3_bucket.my_bucket.id tells terraform that we want to store an image in my S3 named my_bucket. key = "image.png" names the file image.png inside the bucket. and source = "image.png" tells terraform where to find the image.png.

The execution of terraform apply is required once more because modifications were introduced into the configuration file. This re-application is necessary to calculate the difference between the current state and the updated configuration, thereby provisioning and implementing the new infrastructure changes, such as the file upload, into the live environment.

To validate the successful implementation of the updated configuration, the next step was to verify the status using Terraform's output. Specifically, I needed to confirm that the terraform apply command executed without error and that the resulting output confirmed the resource changes were provisioned successfully in the cloud environment. 

![Image](http://learn.nextwork.org/motivated_beige_majestic_sea_cucumber/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
