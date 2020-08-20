## CloudFront Lab

#### Creating the 'Origin'
1. Create a bucket in a region very far away.
2. Keep all properties & permission defaults.
3. Add an image file to the bucket and give it public read access but keep
everything else as default.
4. The image takes ages to load.

#### Setting up the distribution
1. Click 'Create distribution' and choose 'Web'.
2. Under origin name, select the S3 bucket from the dropdown.
3. We want to restrict access to the bucket so that all requests come through
CloudFront, so check yes. This will make extra options appear.
4. Since only the owner can access the S3 bucket, we need to set up and *origin
access identity*. Create a new user.
5. You will need to grant read permissions on the bucket policy too, otherwise
this will not work at all. The default option is no. But check yes.
6. Under default cache behaviour settings, then viewer protocol policy, we can
redirect the HTTP traffic to HTTPS etc.
7. Then under allowed HTTP methods, we can choose what PUT, DELETE, GET etc. The
PUT method gets CloudFront to upload files via edge locations.
8. The 'time to live' or TTL setting are here too. Change the default depending
on how often your data will refresh.
9. We can restrict viewer access to files to only allow users with a signed URL
to connect (cookies).
10. The web application firewall protects you at the application layer.
11. Use default CloudFront certificate for SSL certificate. Then create
distribution.
12. We can access CloudFront using the domain name created in the distribution.

#### Customisations
- If we click on the ID for the distribution, we can add other origins in the Origin tab, this might be another EC2 instance, ELB or something else.
- Under the Behaviours tab, there is information on the path pattern, origin, protocol policy etc.
- Under the Error Pages tab we can create a custom error response for when the origin returns a 4xx or 5xx error code.
- Under Restrictions, we can create geographical whitelists (countries that CAN access content) and blacklists (countries that CANNOT).
- Under Invalidations, we can create new a new invalidation.
Invalidations are about removing your files that are cached in the CloudFront edge locations. I.E. if a file has been changed but there is still an old version of that file cached and you don't want to wait for the TTl to expire, you can manually create an invalidation to remove this although *you will be charged a fee*.

#### Managing S3 permissions
1. Go to S3 file and go to the Permissions tab.
2. Remove public access.
3. Retrieve the domain name from the distribution.
4. Input the domain name instead of the AWS S3 URL. Initially, this image won't be cached in an edge location, so will load slowly.

#### Deleting everything
Go to distributions, select the distribution and click 'Disable' and confirm. This can take up to 15 minutes. Once this has completed, we can 'Delete' the distribution.
