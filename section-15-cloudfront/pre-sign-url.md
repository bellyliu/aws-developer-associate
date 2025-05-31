# Overview
Many companies that distribute content over the internet want to restrict access to documents, business data, media streams, or content that is intended for selected users, for example, users who have paid a fee. To securely serve this private content by using CloudFront, you can do the following:
Require that your users access your private content by using special CloudFront signed URLs or signed cookies.
Require that your users access your content by using CloudFront URLs, not URLs that access content directly on the origin server (for example, Amazon S3 or a private HTTP server). Requiring CloudFront URLs isn't necessary, but we recommend it to prevent users from bypassing the restrictions that you specify in signed URLs or signed cookies.

# How to serve private content

To configure CloudFront to serve private content, do the following tasks:
1. (Optional but recommended) Require your users to access your content only through CloudFront. The method that you use depends on whether you're using Amazon S3 or custom origins:
    - Amazon S3 – See Restrict access to an Amazon S3 origin.
    - Custom origin – See Restrict access to files on custom origins.
    - Custom origins include Amazon EC2, Amazon S3 buckets configured as website endpoints, Elastic Load Balancing, and your own HTTP web servers.
2. Specify the trusted key groups or trusted signers that you want to use to create signed URLs or signed cookies. We recommend that you use trusted key groups. For more information, see Specify signers that can create signed URLs and signed cookies.
3. Write your application to respond to requests from authorized users either with signed URLs or with Set-Cookie headers that set signed cookies. Follow the steps in one of the following topics:
    - Use signed URLs
    - Use signed cookies
If you're not sure which method to use, see Decide to use signed URLs or signed cookies.

# Cloudfront Signed URL Diagram
<img width="861" alt="image" src="https://github.com/user-attachments/assets/0fec311c-87a1-4d6d-81d8-6cf48edfd7bb" />

# Cloudfront Signed URL vs S3 Pre-Signed URL
### Cloudfront Signed URL
- Allow access to a path, no matter the origin
- Can filter by IP, path, date and expiration
- Can leverage caching feature
- Account wide key-pair, only the root can manage it
<img width="550" alt="image" src="https://github.com/user-attachments/assets/90ac3aed-b5af-4b25-9e53-845eb6f53b24" />


### S3 Pre-sign URL
- Issue a request as the person who pre-signed URL
- Use the IAM key of the signing IAM principal
- Limited lifetime
<img width="378" alt="image" src="https://github.com/user-attachments/assets/c1c8ecaa-dafb-4c35-b5e0-c9df21a71272" />

