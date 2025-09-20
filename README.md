# Static Website Hosting on AWS S3 + CloudFront

## 📌 Project Overview
This project demonstrates how to **host a static website** using **Amazon S3** and **CloudFront**.  
A static website contains only HTML, CSS, JavaScript (no backend server needed).  

By the end of this project:
- The website files are stored in **Amazon S3**.
- **CloudFront CDN** is used to deliver content quickly and securely across the globe.
- The website is accessible through a **public URL**.

## 🛠️ AWS Services Used
- **Amazon S3** → To store static files (HTML, CSS, JS, images).
- **Amazon CloudFront** → Content Delivery Network for speed and security.
- **IAM** → To manage access permissions.
- **(Optional) Route 53** → For custom domain (not mandatory).

## 🚀 Steps to Host the Website

### 1. Create an S3 Bucket
- Go to AWS Console → S3 → Create bucket.
- Name it (must be globally unique, e.g., `my-s3-static-site-2025`).
- Uncheck “Block all public access” (since this is a public website).
- Enable **Static website hosting** in bucket properties.
- Note the **bucket endpoint URL**.

### 2. Upload Website Files
- Upload `index.html`, `about.html`, `contact.html`, and any CSS/JS files.
- Ensure `index.html` is the **root document**.

### 3. Set Permissions
- Add a **Bucket Policy** to allow public read access:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-s3-static-site-2025/*"   (our bucket name)
    }
  ]
}
````

### 4. Create CloudFront Distribution

* Go to **CloudFront → Create Distribution**.
* Origin: Select your S3 bucket.
* Default Root Object: `index.html`.
* Enable **OAC (Origin Access Control)** for secure bucket access.
* Create distribution and note the **CloudFront URL**.

### 5. Test the Website

* Open the **S3 bucket endpoint** or **CloudFront URL** in a browser.
* You should see your website live! 🎉

### 6. Output
* [Home page ScreenShot](https://github.com/sathya-selvz/MyS3Website-using-AWS/blob/main/Screenshot%20(32).png)
* [About page Screenshot](https://github.com/sathya-selvz/MyS3Website-using-AWS/blob/main/Screenshot%20(33).png)
* [Contact page Screenshot](https://github.com/sathya-selvz/MyS3Website-using-AWS/blob/main/Screenshot%20(34).png)

## 🧪 Common Errors & Fixes

* **Access Denied** → Check S3 bucket policy or CloudFront OAC settings.
* **404 NoSuchKey** → Ensure `index.html` exists in S3 and matches the name.
* **Old content still showing** → Create a CloudFront **invalidation** (`/*`).

---

## 📂 Project Structure

MyS3Website/
├── index.html
├── about.html
├── contact.html
└── styles.css

## 🔑 Key Learnings

* How to use **S3 for static website hosting**.
* How **CloudFront CDN** improves speed and security.
* How to manage **permissions** with IAM and Bucket Policies.
* How to troubleshoot hosting errors.
  
## 🌐 Future Enhancements

* Use **AWS Route 53** to add a custom domain name.
* Add **SSL/TLS Certificate** (HTTPS) using **AWS Certificate Manager**.
* Automate deployment with **GitHub Actions → S3 + CloudFront**.

  


