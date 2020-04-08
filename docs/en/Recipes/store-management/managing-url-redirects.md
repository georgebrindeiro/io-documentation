---
title: Managing URL Redirects
description: "VTEX IO offers a fast and easy way to add, remove and manage your store's URL redirects using Toolbelt, our CLI! Check out now the step by step."
date: "2020-04-08"
tags: ["adding", "removing", "verifying", "managing", "url", "redirect"]
version: "0.x"
git: "https://github.com/vtex-apps/io-documentation/blob/new-docs/docs/en/Recipes/store-management/managing-url-redirects.md"
---

# Managing URL Redirects
  
The **URL redirect** is very advantageous when you want a given web page's accesses to be redirected to another of your choosing. 

You may want to do this for any number of reasons, such as a change to the URL path or for users from a specific region to have access to a custom web page.

No matter the reason: it's likely that your website has already, is currently or will require a redirect from one URL to another.

Therefore, VTEX IO offers a fast and easy way to add, remove and manage your store's URL redirects using Toolbelt, our CLI. Check it out:
  
## Step by step

### Adding redirects

1. Open a `.csv` file of your choosing. You can use Excel or Google sheets, for example;

<div class="alert alert-warning">
The file must be a <code>.csv</code> type file. Otherwise, the redirects upload will not work.
</div>

2. Once opened, create four columns in those files with the following values: `from`, `to`, `type` and `endDate`. For example:

![csv-file-url-redirect](https://user-images.githubusercontent.com/52087100/78804703-dabb8880-7996-11ea-9fa6-2acd8766f67d.png)

- `from` - Original URL i.e. the URL you want to create a redirect *from*;
- `to` - New URL i.e. the URL users will be redirected *to*;
- `type` - Whether the redirect will be `TEMPORARY` or `PERMANENT`;
- `endDate` - Data at which the redirect will expire. Notice that if the redirect is permanent, no value for `endDate` is required.

<div class="alert alert-warning">
<code>TEMPORARY</code> type redirects will receive the <code>302</code> status code, while <code>PERMANENT</code> type ones will receive the <code>301</code> status code.
</div>

3. Fill in the cells under each column with the values desired for your store. Remember that each redirect's data must be entered on different lines, as shown in the example below: 

![urls-redirect-csv-file](https://user-images.githubusercontent.com/52087100/78805256-91b80400-7997-11ea-972f-bac24c60cf3c.png)

4. Save and name the document as desired;
5. Using your terminal and the [VTEX IO Toolbelt](https://vtex.io/docs/recipes/development/vtex-io-cli-installment-and-command-reference), log into your VTEX account;
6. Once logged in, run the `vtex redirects import {fileName}.csv`, replacing `{fileName}` with the name of the file that you've just saved.

After the sixth step, Toolbelt will receive the file and save its information in VBase, the VTEX IO data bank. Accordingly, the redirects will take effect.

### Removing redirects

1. Using your terminal and [VTEX IO Toolbelt](https://vtex.io/docs/recipes/development/vtex-io-cli-installment-and-command-reference), log into your VTEX account;
2. Once logged in, run the `vtex redirects delete {URL}`, replacing`{URL}` with the URL that will have its redirect removed.

<div class="alert alert-warning">
The URL that is sent when running <code>vtex redirects delete {URL}</code> will have its redirect removed so it must be one of URLs from the `from` column of the <code>.csv</code> type file.
</div>

### Verifying redirects

To check the site redirects that are saved on the platform's data bank, simply log into your VTEX account and run `vtex redirects export {fileName}.csv` , replacing `{fileName}` with the name of the `csv` file holding the site redirects. 

This will tell Toolbelt to return the full list of saved redirects to your local files.
