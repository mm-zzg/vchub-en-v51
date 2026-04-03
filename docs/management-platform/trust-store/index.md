# Trust Store

The **Trust Store** is used to display and manage digital certificates in the system. It supports operations such as viewing certificate details, importing new certificates, and deleting existing ones.

Certificates uploaded to the Trust Store are trusted root or intermediate certificates containing public keys. These are used to verify the authenticity of remote certificates.

When establishing a connection (such as during redundancy or networking), the system checks whether the remote certificate's chain can be validated against any certificate in the Trust Store.

If the remote certificate itself or any certificate in its chain exists in the Trust Store and a valid trust chain can be established, the remote certificate is considered trusted.

Click **“Node” → “Trust Store”** to display the certificate list.

![alt text](18.png)


If a certificate is due to expire within 30 days, the **Expiration Time** will be shown in red to alert the user to update it in time.

![alt text](19.png)


If a certificate is already expired, an **“Expired”** label will appear next to its expiration date.

![alt text](20.png)


## Import Certificate

Click the **“Import”** button to select and upload a certificate file. Upon successful import, the new certificate will be listed automatically.

Supported certificate formats:

1. `.der`
2. `.cer`
3. `.pem`
4. `.crt`

## View Certificate

Click the **“View”** button on a certificate row to open a detailed view of the certificate’s information and properties.

![alt text](21.png)


## Delete Certificate

Click the **“Delete”** button next to a certificate to remove it. A confirmation dialog will appear before deletion.

![alt text](22.png)


**Notes**

- Expired certificates may pose security risks. Please update them promptly.
- Before deleting a certificate, ensure that doing so will not affect system functionality.
