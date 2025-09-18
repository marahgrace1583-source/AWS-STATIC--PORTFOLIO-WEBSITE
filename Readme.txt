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

![2025-08-11 (1).png](attachment:f4eab6c4-3d22-4e81-8ea4-52544e41fca5:0f2bafa1-2c8d-4a4b-8b83-5480f24553ea.png)

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

![2025-08-13 (2).png](attachment:123db909-fc35-4f1c-89ba-244d7ad68534:6cb70aa4-a86c-4f07-8cfe-8c9c13a60b03.png)

![2025-08-13 (5).png](attachment:a1cf539d-64a7-44b1-906b-b9835bb409da:683820ae-d802-4274-8ebe-145b5f45d3bb.png)

![2025-08-13 (6).png](attachment:8766763c-8e7f-4ae9-8fdf-a5ba1b30ac70:38f3fc1b-fdc3-4315-bbff-5adf66105014.png)

## **Step 3: Create S3**

Create route 53 for domain name registration 

1. Go to route 53 ,create hosted domain ,ad d your domain name from name cheap 
2. go to name server and choose   custom DNS 
3. copy the name server that was generated from route 53 and update on domain name  **NAMECHEAP**
4. and paste it on the name server and  save 

![2025-08-13 (14).png](attachment:c0a3302d-ada2-4801-a74c-e621d5d2ec4f:83062f2a-6a8b-400b-839b-f2815c3b04fd.png)

![2025-08-14 (25).png](attachment:ec6fdcdc-512f-4506-b038-28c1edec958a:49eadfa6-16ea-4b53-af3f-60fc2778ed06.png)

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
