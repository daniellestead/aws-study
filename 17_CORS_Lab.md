## CORS Lab
(Cross origin resource sharing)

*Basically just allowing code in one bucket to access the code in another.*

1. Create a bucket with public read access.
2. Under Properties, we want to enable 'Static website hosting' and select 'Use
t'his bucket to host a website'. It will ask the names of the error document and
index document.
3. Upload the files into the S3 bucket, and grant these public access.
4. Delete the loadpage.html script from that bucket and create a new bucket with
public read access and do the static website hosting thing again.
5. Upload the loadpage.html file to the new bucket. The DNS endpoint is found
under the static website hosting bit.
6. The index.html script references the loadpage.html, so we need to change the
path in the index.html script to point to the DNS endpoint.
7. Copy the endpoint for the bucket used to host the webpage and go back into
the other bucket's Permissions section.
8. Click the 'CORS configuration' button. In the <AllowedOrigin> section it
currently has *, but we replace this with our URL and hit Save.
