# Lipa na MPESA STK Push Integration with Daraja API and PHP

MPESA is one of the most convenient ways people make transactions in Kenya. MPESA has come a long way from just sending and receiving money to making payments to businesses. You can now integrate MPESA into your online business for faster transactions with your customers.

## What is MPESA Daraja API?

MPESA Daraja API is a powerful tool provided by Safaricom, Kenya's leading mobile network operator. It allows developers to interact with MPESA's mobile payment platform, enabling seamless transactions, account management, and other financial services.

## MPESA STK Integration on Daraja

Firstly, What is STK push? STK Push is a prefilled pop-up notification on a customer's MPESA Menu to confirm the initiated transaction by the merchant by inputting their PIN.

In MPESA STK API integration, the M-Pesa registered customer gets a pop-up notification to confirm the initiated transaction by the merchant. The transaction is then processed after the customer keys in their MPESA PIN and confirms the transaction. Both the customer and merchant get transaction confirmation messages. 

Now that we know the types of MPESA Integration services, the next step is to make sure that we have an account with Safaricom Developers Account. To create an account, visit the [Daraja Safaricom website](https://developer.safaricom.co.ke/). If you have an account with Safaricom Daraja, you can log in; otherwise, sign up.

The next step is to create a new sandbox app by clicking on the "Add a New App" button and giving it a name. Ensure you select both Lipa na Mpesa Sandbox and Mpesa Sandbox and hit the "Create App" button. You will get the following success message. Awesome! Now that we have our app created successfully. Click on your newly created app.

## MPESA Daraja Menu

The Consumer Key and Consumer Secret are personal and therefore should be secured and not shared.

## How to Integrate Lipa na MPESA STK Push in PHP

Firstly, let's set up your MPESA API Folder: `mpesa`.

### I. Checkout Page (checkout.php)

The checkout page, (checkout.php), is a sample checkout page for testing the API.

### II. Express STK API File (express-stk.php)
When the customer enters the phone number and presses SEND, the POST request will be handled by an external PHP file in the API folder: express-stk.php.

At the end of the transaction, the user is redirected to the page confirm-payment.php, which confirms if the transaction was successful or not.

### III. Callback File (callback.php)
Note that the response on the transaction status (whether the customer PAID, CANCELED, or if there was an ERROR) is sent by Safaricom API to your callback URL. To implement this, the callback URL is supposed to receive this response from Safaricom. Therefore, you need to set up the code in the callback URL such that it receives the response in the form of JSON data and then stores it in your database.

Your database will have the following columns: MerchantRequestID, CheckoutRequestID, ResultCode (0 means successful processing and any other code means an error occurred or the transaction failed), ResultDesc, MpesaCode, TransactionDate, and PhoneNumber.

### IV. Payment Confirmation Page (confirm-payment.php)
Back to the user end, after the STK push is initiated, the user is redirected to the confirmation page confirm-payment.php, which should be close to something like this:

When the user clicks "Confirm Payment," we initiate an MPESA Transaction status query to check the status of the transaction (To see if the user actually PAID, CANCELED, or if there was an ERROR). This is handled by: status.php.


## Conclusion
This article provides a comprehensive guide on integrating MPESA STK Push into your PHP website. With the provided code examples and explanations, you can enhance your website's payment capabilities and provide a seamless experience for your customers.
