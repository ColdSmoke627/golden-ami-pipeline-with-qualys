# ami_golden_pipeline_qualys

THIS SCRIPT IS PROVIDED TO YOU "AS IS." TO THE EXTENT PERMITTED BY LAW, QUALYS HEREBY DISCLAIMS ALL WARRANTIES AND LIABILITY FOR THE PROVISION OR USE OF THIS SCRIPT. IN NO EVENT SHALL THESE SCRIPTS BE DEEMED TO BE CLOUD SERVICES AS PROVIDED BY QUALYS

# Summary
We extended AWS GOlden AMI Pipeline by working with AWS Solution Architects team to help customers detect and fix critical vulnerabilities and compliance issues in the image creation pipeline, before they reach production environments and throughout the instance lifecycle.

AWS team documented it in their blog (https://aws.amazon.com/blogs/apn/creating-a-golden-ami-pipeline-integrated-with-qualys-for-vulnerability-assessments/), today we published it Qualys blog (https://blog.qualys.com/news/2019/02/06/assess-vulnerabilities-and-misconfigurations-in-aws-golden-ami-pipelines-with-qualys). 
In addition, Qualys documented the approach and automation templates in Qualys Cloud Security GitHub repository, so users can easily follow the documented steps and run the cloud formation templates to setup Qualys scanning of instances in a golden AMI pipeline. 

This process includes scanning for vulnerabilities in the pipeline using Qualys Scanners, embedding Qualys Agents into the AMI for continuous security and incorporating an approval process to create secure Golden AMIs. Optionally, the user can enable Qualys Policy Compliance scanning in the pipeline as well by supplying the required SSM variable values outlined in the instructions - AWS Golden AMI Pipeline Reference Architecture with Qualys.pdf - located in this repo (https://github.com/Qualys-Public/golden-ami-pipeline-with-qualys/blob/master/AWS%20Golden%20AMI%20Pipeline%20Reference%20Architecture%20with%20Qualys.pdf)

# Implementation
The information required to implement the pipeline is contained in the PDF file "AWS Golden AMI Pipeline Reference Architecture with Qualys.pdf" (https://github.com/Qualys-Public/golden-ami-pipeline-with-qualys/blob/master/AWS%20Golden%20AMI%20Pipeline%20Reference%20Architecture%20with%20Qualys.pdf). The PDF outlines all of the configuration information and data required from your Qualys subscription that is used to buildout the pipeline and automation docs. For additional information on the AWS configurations look in the file "Golden-AMI-Pipeline-Guide V1.2.docx" (https://github.com/Qualys-Public/golden-ami-pipeline-with-qualys/blob/master/Golden-AMI-Pipeline-Guide%20V1.2.docx)

# Pipeline Implementation Simplified Overview Steps
1. Gather the required information outlined in "AWS Golden AMI Pipeline Reference Architecture with Qualys.pdf" and "Golden-AMI-Pipeline-Guide V1.2.docx"
2. Run the CloudFormation Template ami_golden_ami_pipeline_qualys-vm-pc.json and enter the required information 
3. Provide instructions for submitting candidate AMIs via the SSM Automation document created by the CloudFormation Template to devops teams
4. Approve / Reject candidate AMIs based off the scan findings in Qualys
5. Approved AMIs are automatically reevaluated on the configured schedule
