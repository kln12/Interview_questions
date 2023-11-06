**1.Define statefile   
Answer**   When you run terraform apply command to create an infrastructure on cloud, Terraform creates a state file called “terraform.tfstate”. This State File contains full details of resources in our terraform code. When you modify something on your code and apply it on cloud, terraform will look into the state file, and compare the changes made in the code from that state file and the changes to the infrastructure based on the state file.  
$$$$ https://www.easydeploy.io/blog/terraform-state-file/   
**2.write the samele S3 resource file    
Answer**   resource "aws_s3_bucket" "example" {
  bucket = "my-tf-test-bucket"

  tags = {
    Name        = "My bucket"
    Environment = "Dev"
  }
}
   
**3.terraform state lock   
Answer**That is not what state locking is for. State locking is for locking the state during a deployment such that no two terraform processes try to update the same state at the same time.   
That has nothing to do with protecting your resources from changes by other developers. That is something you need to handle at an organizational level, maybe through differently permitted users, maybe by having separate accounts, code reviews to prevent accidental destruction, maybe SCPs   

https://spacelift.io/blog/terraform-files   
