---
title: How NOT to send a bank account statement to the customer
author: Srinivasan Rangarajan
date: 2016-06-01
url: /bank-account-statement/
aliases: 
  - /bank-account-statement/
  - /how-not-to-send-a-bank-account-statement-to-the-customer/
categories:
  - Security

---
I have a few bank accounts and there is this particular local bank called [City Union Bank][1], that is more than hundred years old.

I received an email from that bank which has a list of different new features that they have added for the benefit of the customers, using latest technology that they could get their hands on &#8211; like self service branches, mobile banking using android apps, missed call balance enquiry, and many more.

<!--more-->

> <span style="color: #0000ff;">To enable our customers to have banking facilities from anywhere and anytime, our bank has implemented various e-initiatives. One such facility is E-Statement of account in HTML format. The HTML form of the E-Statement of your account for the month of April 2016 is enclosed for your use.</span>

And, yes their email was in blue, green and brown colors. And they had attached a plain HTML file with the email.

Before I could even finish reading the entire email, I open the file by clicking and letting gmail open in it&#8217;s attachment viewer. And it threw this error in my face:

> ## Please download the statement and view it in browser

Ookkkayyy! So I go download it and open only to see it asking me for a password.

<a href="http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password.png" rel="attachment wp-att-38"><img class="aligncenter size-medium wp-image-38" src="http://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password-300x82.png?fit=300%2C82" alt="bank-statement-password" srcset="http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password.png?resize=300%2C82 300w, http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password.png?resize=600%2C163 600w, http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password.png?resize=250%2C68 250w, http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/11/bank-statement-password.png?w=606 606w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /></a>

I go back to the email and read the section which says what my password is.

> **<span style="color: #0000ff;">Your Statement is password protected. Please enter your Customer ID as the  password to open the Account Statement.</span>**

But there is one little problem. When I signed up for an online netbanking account with this bank, I was given the choice of either logging in with some weird 7 or 8 digit number that I won&#8217;t remember for the rest of my life or choosing my own personalised username. Naturally I chose my own username and conveniently forgot the customer ID.

So in order to login I have to type my customer ID and I am now lost without access to my own bank statements.

Or am I really?

### Password Protected HTML??

If it were some password protected PDF file, I would have given up all hope and forgotten about it. But the bank had sent my statement in a HTML file with password protection.

So I quickly &#8220;View Source&#8221;&#8216;ed the page and see gibberish. They had used some weird encryption for the raw HTML and have a small javascript snippet to decrypt it. Should I waste time reverse engineering the encryption and get back the actual source? But if the browser has loaded the page and shows a password screen, it means the browser has already decrypted it and I can look at the DOM and see what they do.

Those who know basic HTML/Javascript can guess where I am going with this. All I had to do was

  1. goto View > Developer > Developer Tools
  2. Cmd + F and search for &#8220;password&#8221;
  3. ???
  4. Profit!!!<figure id="attachment_43" style="width: 579px" class="wp-caption aligncenter">

<a href="http://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2016/06/cub-password-1.png" rel="attachment wp-att-43"><img class="size-full wp-image-43" src="http://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2016/06/cub-password-1.png?fit=579%2C395" alt="City Union Bank Password in HTML" srcset="http://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2016/06/cub-password-1.png?w=579 579w, http://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2016/06/cub-password-1.png?resize=300%2C205 300w" sizes="(max-width: 579px) 100vw, 579px" data-recalc-dims="1" /></a><figcaption class="wp-caption-text">Hidden in Plain Sight</figcaption></figure> 

All that is left for me to do is use the super secret password and login to see my account statement.

And since emails aren&#8217;t secure, anybody can get hold of my private information and I don&#8217;t even want to think about the various ways they can target me.

I want to meet the person who thought this was a great idea and get a list of other things he helped design, so that I can be careful. I thought banking software/servers audited for security regularly. If this bank was also audited, I want to meet the person who signed off on this. Is our bank account really secure?

If this is how banks and financial institutions are going to protect our money, I don&#8217;t even want to know what other government departments are doing with our personal and private data (read [Aadhaar][2]).

The future looks rather bleak to me.

**PS:** The balance they showed in that statement was completely different from the balance I had in account. Guess I should close this account and short sell this bank stocks if I can.

 [1]: http://www.cityunionbank.com/
 [2]: http://uidai.gov.in/