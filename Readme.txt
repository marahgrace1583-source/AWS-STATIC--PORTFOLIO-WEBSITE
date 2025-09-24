**S3 Static Website with CloudFront & Namecheap Domain**

In this guide, we'll demonstrate how to host a basic website on AWS S3. 
You'll upload your website files (such as index.html, images, and CSS files) into an S3 bucket and configure it for public access online.

Why Choose AWS S3?
AWS offers multiple website hosting options. Amazon EC2 is one alternative, providing a virtual server with complete installation freedom.
However, EC2 requires more configuration, ongoing maintenance, and typically costs more than S3, particularly for small or simple websites.

Easy – Just upload files, set permissions, and you’re live.
•	Scalable – Can handle a few visitors or millions without extra work.
•	Cost-effective – You only pay for the storage and traffic you use.

## **Project Documentation:**

## **Project Overview**

- **Project Name:** marahs Static Website
- **Purpose:** Host a static website on AWS S3, accelerate delivery with CloudFront, and connect a custom domain from Namecheap.
- **Tools:** AWS S3, AWS CloudFront, Namecheap DNS,ROUTE 53,CLOUD FRONT
- **Status:** Completed / In Progress / Testing
- **Author:** Amarachi nnadi

## **Tools Used**

1. **VS Code** – Code editor for HTML/CSS/JS.
2. **Live Server (VS Code Extension)** 
3. **AWS Management Console** – S3, CloudFront configuration.

## **Step 1: Prepare Website Template**

**Description:** Customize the downloaded template to fit project requirements.

**Steps:**

1. Extract website template.
2. Open the folder in **VS Code**.
3. Install **Live Server** extension.
4. Edit HTML/CSS/JS to your taste.
5. **Image Issues:** Resize or convert images to 

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/71cd0797425f6ac80de99eda729ede1b86bfc1c7/Screenshot%202025-09-24%20113616.png)

## **Step 2: Create S3 Bucket**

**Description:** Set up an AWS S3 bucket for static website hosting.

**Steps:**

1. Go to AWS S3 → Create Bucket.

create the bucket and upload the content into the bucket ,check on the bucket you created 

and upload file .

check on add file and upload 

1. **Bucket Name:** **marah-134125631258-web-content**
2. **Region:** Europe stockhalm
3. **Settings:**
    - Uncheck “Block all public access
    - Go to properties and enable **Static website hosting**
        - Index document: `index.html`
        - Error document: `error.html` (optional

then go to permission and edit bucket policy where you make your statement 

**NB if you make bucket public you will have to give it a certain permission like GETOBJECTONLY**

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/f94017d86b3a378c6376b7cbcc2adc5599daaafa/Screenshot%202025-09-24%20114045.png)

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/6a002a431a94e44df94479bdb49c7da3525085db/Screenshot%202025-09-24%20114756.png)

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/8623b35db4a6afca325aa22f434b599e90cac90e/Screenshot%202025-09-24%20115030.png)

## **Step 3: Create S3**

Create route 53 for domain name registration 

1. Go to route 53 ,create hosted domain ,ad d your domain name from name cheap 
2. go to name server and choose   custom DNS 
3. copy the name server that was generated from route 53 and update on domain name  **NAMECHEAP**
4. and paste it on the name server and  save 

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/06902d946b5b4fe77d9825f58ac4b4e95ba6e966/Screenshot%202025-09-24%20115710.png)

![image alt](https://github.com/marahgrace1583-source/AWS-STATIC--PORTFOLIO-WEBSITE/blob/31ddde4459900c26040d718fbff0381b79920e1b/Screenshot%202025-09-24%20121922.png)

## **Step 4: Create cloud front**

create a CloudFront for a content delivery network in a nearby edge location 

step

1.Go to CloudFront and on the top blue print click on create distribution page 

check on origin name add your domain name ,

use website end point 

1. Check WAF is not enabled. Add item and request a certificate. Add domain name and another domain name (I used WWW) OPTIONAL  ,click create record and allow the certificate to be issued took about 15mins

![2025-08-13 (18).png](attachment:f724d3a0-1955-484f-b617-afaea42a64fb:94167ae0-ada7-44b0-bc5d-077644621f07.png)

![2025-08-14.png](attachment:ca65f080-c4a2-41b7-a294-1991ae12fca6:5285b900-bc90-4ed8-921e-dca91e16c2d6.png)

## step 5 creating distribution point

step 1 Go back to CloudFront,click create distribution page 

check origin domain and use the end  point 

step 2 go to your WAF and check do not enable security protection 

add item i added **www .** my domain name because i did it from scratch, check the custom SSL distribution , 

step 3 then go back to your route 53 and click on hosted zone, click on your name,  create record  and open alias ,check on your route traffic alias cloud front distribution ,copy your cloudfront distribution and paste it on the cloud front distribution

step 4 check on add another  record ,add your subdomain and add your www.with your domain name ,open alias choose cloud front distribution add distribution and create record 

![2025-08-14 (29).png](attachment:d809a4cc-6ff0-47ce-a7af-43bd761c8178:2025-08-14_(29).png)

## step 6 **Test & Verify**

![2025-08-14 (32).png](attachment:72f057e9-7360-4523-a5d9-4f043669b746:2025-08-14_(32).png)

## **Conclusion**

- The S3 static website project was successfully deployed with **CloudFront** for fast content delivery and a **custom Namecheap domain** for professional access.
- All website files are now publicly accessible via HTTPS.
- The workflow demonstrates a **full static website deployment pipeline** using AWS services and domain management.

## Lessons Learned

- ACM certificates for CloudFront must be created in `us-east-1`.
- S3 needs CloudFront for HTTPS when using a custom domain.
- DNS propagation can take time, so patience is important.
