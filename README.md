# Hosting_resume_on_aws_s3 

## Step 1: Upload Resume to S3 and Configure Static Website Hosting

1. Create an S3 Bucket:
    Go to the S3 console and create a new bucket (jyothi-bucket-for-resume-hosting).
2. Upload your resume (PDF or HTML) to the S3 bucket.
   If using an HTML file, you may need to upload any associated files (like CSS, images).

![image](https://github.com/user-attachments/assets/d06505bd-7eba-4f6a-b7e5-ab09b804aabb)

3. Configure Bucket for Static Website Hosting:
     Under the bucket settings, enable Static website hosting.
     Set the index document to the main file of your resume (e.g., index.html).

![image](https://github.com/user-attachments/assets/4edfdd15-efe1-49d6-81c1-48f86fe23596)

4. Make the Bucket Public:
  Update the bucket permissions to allow public access to your resume file.
  Add a Bucket Policy to allow public GetObject access for the static website.

![image](https://github.com/user-attachments/assets/a582d8c9-7314-42c9-954f-c1c3e8aa214e)

5. Now access the static website URL to see resume

![image](https://github.com/user-attachments/assets/85595567-65d9-44f2-a7f2-db94bc8ff1ef)

# Hosting_resume_on_aws_s3_with_cloudfront
## Step 2: Set Up CloudFront Distribution
Before setting up cloudfronfron 
. Disable s3 static website hosting
. Block all public access on S3 bucket
. delete bucket policy

1. Create a CloudFront Distribution: Go to the CloudFront console and select Create Distribution.
2. Specify S3 Bucket as Origin:
    In the origin settings, select your S3 bucket as the origin domain.
    Set Restrict Bucket Access to Yes for added security.
    CloudFront can automatically set up an Origin Access Identity (OAI) to secure the content.
   
Note: Add Default root object (html file or pdf). 

![image](https://github.com/user-attachments/assets/118ca7cb-6285-49aa-a5e7-6b995d9f16c9)

4. Create the CloudFront distribution and wait for deployment (it may take a few minutes).
5. Update the s3 bucket policy by coping the policy from cloudfront (Only cloudfron have GetObject on s3 bucket )

![image](https://github.com/user-attachments/assets/ff891c4e-3f64-4065-85f0-151c4fda7bf9)

![image](https://github.com/user-attachments/assets/70027b94-50bd-4e32-8368-0dbad39a5143)


5. After deployment, you’ll receive a CloudFront URL (e.g., https://xxxx.cloudfront.net) to access your resume.


![image](https://github.com/user-attachments/assets/871791e3-71ea-4bbe-be27-c1859a46ceaa)



