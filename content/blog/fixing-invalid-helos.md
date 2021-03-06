---
title: Fixing Invalid HELO’s
author: Major Hayden
type: post
createdAt: 2006-12-27T03:02:40+00:00
description: >-
    You did your research and made a great options trade, but now it is a
    losing trade. What can you do now?
url: /2006/12/26/fixing-invalid-helos/
dsq_thread_id:
  - 3642764602
categories:
  - Blog Posts
tags:
  - mail

---
If your server is spewing an invalid HELO, you could be blacklisted pretty quickly. The [Spamhaus SBL-XBL][1] list and [CBL][2] list work together to find servers announcing themselves improperly.

The common reasons why mail servers are blocked for bad HELO's are:

  * Server is announcing itself as &#8220;localhost&#8221;.
  * Server is announcing itself as an IP address.
  * Server is announcing itself as a hostname that does not exist.

Are you unsure what your server's announcing itself as? Try these:

  * Send an e-mail to helocheck@cbl.abuseat.org. You will get an immediate response with exactly what your HELO contains.
  * Telnet to port 25 on your mailserver. Run `telnet mail.yourdomain.com 25` and wait a few seconds. Your server's HELO message should appear.

So your server is announcing itself as the wrong thing? Well, fix it!

**Managing HELO with QMail**

If **/var/qmail/control/me** exists, edit it so that it matches your reverse DNS record for your server's primary IP address. If the file doesn't exist, you can create the file and add the correct hostname to it, or adjust your hostname on your operating system. Try running `hostname mail.yourdomain.com` to fix things immediately, and edit the proper configuration files to correct your hostname at boot time.

**Managing HELO with Postfix**

The default value for Postfix's HELO is the value of `$myhostname`. If that variable is defined in the main.cf, adjust it so that it matches the reverse DNS record of your server. If it isn't defined in main.cf, then adjust the hostname on your operating system. Try running `hostname mail.yourdomain.com` to fix things immediately, and edit the proper configuration files to correct your hostname at boot time. Should neither of those methods suffice on your server, simply adjust the `smtp_helo_name` variable to match the reverse DNS record of your server. For example:

<pre lang="html">smtp_helo_name = mail.yourdomain.com</pre>

**Managing HELO with Sendmail**

Adjust the hostname on your operating system. Try running `hostname mail.yourdomain.com` to fix things immediately, and edit the proper configuration files to correct your hostname at boot time.

 [1]: http://www.spamhaus.org/
 [2]: http://cbl.abuseat.org/