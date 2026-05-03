# DNS record change guide

*Where to view this portfolio piece: on this page.*

---

I previously worked in the support at [Fastmail](https://www.fastmail.com/), where a big part of my role was ensuring customers had access to accurate, timely and accessible information about Fastmail services and products. While Fastmail is primarily an email service, thousands of customers also use Fastmail to host websites. 

At one point, Fastmail engineers were making some configuration changes to the networks responsible for hosting user websites, which would cause the IP addresses that customers were using to host their websites on to change. While we could manage the required changes internally for users hosting their DNS records at Fastmail, users that were hosting their DNS records externally would need to make changes on their end.

To faciliate this, I wrote guides to outline the specific steps customers would need to take to ensure their websites remained online. Configuing DNS records can be tricky at the best of times, and from experience I knew that the processes and terminology used typically varied between DNS hosts. So, instead of providing a generic set of instructions, I analysed the DNS records of affected customers to identify the most commonly used DNS hosts, and then worked through and documented the steps for making the required changes for the most popular hosts.

These guides, sent out to thousands of customers, were successfully followed, with over 90% of customers making the required change without any additional support.

Here's a (redacted) version of the guide I wrote that was sent to a customer. This particular message was sent to a customer with:

- Only one website hosted at Fastmail.
- Their DNS hosted by Cloudflare.

---

> Dear **$customer_name**,
>
> Our systems show that you are currently hosting a website on your Fastmail account. They also show that the DNS for this website is hosted at Cloudflare, an external DNS provider. As a result of some upcoming technical changes on our end, we’ll need you to update the DNS records for this domain at Cloudflare if you wish to continue hosting this website at Fastmail. 
>
> For context, when you set up a domain so that it can be used to access a website, you typically enter the IP addresses of the web server hosting your website. Because you are using an external DNS provider for your domain, the IP addresses of the Fastmail web server have been entered on the external DNS provider's (Cloudflare's) control panel. These IP addresses are changing, and you will need to update them at Cloudflare by **$3_months_time**. 
>
> We have identified the following domains that need updating:
>
> - **$example.tld**
>
> As mentioned above, the DNS for this domain appears to be hosted by Cloudflare. Cloudflare supports a feature called "CNAME flattening", which we recommend using instead of specific IP addresses.
>
> To set this up, please follow these steps:
>
> 1. Log in to your [Cloudflare dashboard](https://dash.cloudflare.com/login).
> 2. Click on your **$example.tld** domain in the domain list.
> 3. Go to **DNS > DNS Records** at the top right of the screen. For each **$example.tld** record, you should see one or more A type records with content of the form **$current_ip** .
> 5. If there is more than one A type record for **$example.tld** , click **Edit** and then **Delete** on each of them until there is only one A record left.
> 6. Click **Edit** on the final A record for **$example.tld**.
> 7. Change the **Type** to **CNAME**, and change the **Target** to **web.fastmail.com**.
> 9. Ensure **Proxy status** is set to **DNS only**.
> 10. Click **Save**.
> 
> The DNS for your domain will now point to our new IP addresses. These changes should not cause any interruption to the access of your website.
>
> Please note that if the described changes are not made by **$3_months_time**, your domain will no longer point to your website content, and the website will no longer be accessible via the domain. The content of your website will still exist in your account, but anyone who enters **$example.tld** online will not be able to view your website.
>
> If you have any questions about this change, or any of the steps you need to take, please reply to this message. We're always happy to help.

