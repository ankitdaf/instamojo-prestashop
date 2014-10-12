Installation steps
===================

Creating a link
---------------

1. Log in to Instamojo, and create a link under the Services / Membership Type
2. Add a title, description, and a minimum value (10 is the least you can enter. **Don't make it zero**)
3. Enable "Pay what you want"
4. In the Advanced Settings section, go to the "Custom Redirection URL", and enter : http://yourdomain.com/modules/instamojo/validation.php
5. Save the link


Custom Fields
--------------

Prestashop assigns an id to each shopping cart, which it needs to get back from the Payment Gateway (Instamojo). So, you must create a custom field on Instamojo

1. Navigate to the Instamojo Dashboard at https://www.instamojo.com/dashboard/, find the link you just created, and click on "Custom Fields"
2. Enter "TransactionId" (without the quotes) as the field name, make it Required, and click Save. Place your mouse pointer on the field name, you'll see something like Field_1111 (the number will be different). Note that down
3. Copy that into the file here : `modules > instamojo > lib > Config.php` in the variable `TXN_ID_NAME`.


HTML Code
---------

1. Get the HTML code for the Instamojo button for your website (it's different for every merchant) by finding your link in the Instamojo Dashboard and clicking on "Payment Button".
2. Put the above HTML code in the file here : `modules > instamojo > views > templates > front > instamojo.tpl`. Replace the code within the `<p> .. </p>` tags. Add the following code to the end of the `href` URL: `?embed=form&data_name={$imname}&data_amount={$imamount}&data_phone={$imphone}&data_email={$imemail}&data_{$imcustom}={$imtid}&data_readonly=data_amount&data_readonly=data_{$imcustom}&data_hidden=data_{$imcustom}`. If you follow this step, you can skip the third step.
3. Alternatively, you can use the file I supplied directly, but with one important change in instamojo.tpl : Replace the link in the href with the correct username, link and `data-token` value.

API parameters
---------------

1. Get your API keys by signing into your Instamojo account and visiting: https://www.instamojo.com/developers/
2. Copy them into the file here : `modules > instamojo > lib > Config.php` in the corresponding fields


Installing into Prestashop
---------------------------

1. Download the zip file by clicking the Download button on the right.
2. Upload the zip file to the "modules" folder on your server running Prestashop, and unzip it.
3. Rename the unzipped folder to "instamojo".
4. Login to the Prestashop backend, and go to the "Modules" section.
5. Search for "Instamojo", the plugin should show up. Click on Install.

That's it, you are done with the installation with Prestashop!

This plugin is live at http://daflabs.com, in case you want to check out how (smoothly) it works

If you have a question, write to support@instamojo.com and they'll help you out.

If you want to pay the author for this though, you can write to him at me@ankitdaf.com , and he will send across an Instamojo link.


License
--------

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Instamojo Plugin for Prestahop</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://ankitdaf.com" property="cc:attributionName" rel="cc:attributionURL">Ankit Daftery</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
