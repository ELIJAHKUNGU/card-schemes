Card schemes

Card schemes refer to the network and rules that govern the use of payment cards, such as credit, debit, and prepaid cards, issued by financial institutions. These schemes set the standards for processing transactions, including authorization, clearing, and settlement. Major card schemes include Visa, Mastercard, American Express, and Discover.

Key aspects of card schemes include:

1. **Transaction Flow**: Card schemes facilitate transactions between cardholders, merchants, issuing banks (which issue cards to consumers), and acquiring banks (which work with merchants to process payments).
  
2. **Fees**: Each transaction typically incurs fees, such as interchange fees, network fees, and merchant service charges, which are distributed between the different participants (issuer, acquirer, card schemes).

3. **Security Standards**: Card schemes enforce security protocols like PCI DSS (Payment Card Industry Data Security Standard) to protect sensitive cardholder data and ensure the secure processing of transactions.

4. **Acceptance**: Card schemes determine where the cards they issue can be accepted. For example, Visa and Mastercard are widely accepted globally, while some other schemes may have regional or limited acceptance.

5. **Interchange Fees**: These are fees that the merchant's bank (acquirer) pays to the cardholder's bank (issuer) for processing a card transaction. Card schemes set the rules around these fees, depending on factors like transaction type (in-store or online), the card used (credit or debit), and even the country where the transaction occurs. Interchange fees are a significant part of the cost of accepting card payments for merchants.

6. **Transaction Types**: Card schemes facilitate multiple types of transactions, including:
   - **Point-of-Sale (POS)**: Traditional in-store payments using a physical card.
   - **Online (e-commerce)**: Card-not-present transactions where the card details are entered manually during an online purchase.
   - **Contactless Payments**: Payments are made by tapping the card or a mobile device against a terminal, often using Near Field Communication (NFC) technology.
   - **Prepaid Cards**: Cards that are preloaded with funds and used similarly to debit or credit cards, but without a line of credit.

7. **Fraud Protection and Risk Management**: Card schemes implement various tools and policies to mitigate fraud. These include:
   - **EMV Chip Technology**: Replacing magnetic stripes with chip-based cards to reduce card-present fraud.
   - **Tokenization**: Converting sensitive card information into unique tokens for secure transactions, especially for mobile and online payments.
   - **3D Secure (3DS)**: A protocol for online transactions where cardholders are authenticated via additional layers of security, such as one-time passwords (OTP) or biometric verification.
   
8. **Dispute Resolution and Chargebacks**: Card schemes define the rules for handling disputes between cardholders and merchants. A chargeback occurs when a cardholder disputes a transaction, and the card issuer reverses the charge. Schemes provide a framework for reviewing and resolving such disputes.

9. **Global vs. Local Schemes**: 
   - **Global Schemes**: Visa, Mastercard, and American Express dominate worldwide, allowing cardholders to make payments in almost any country.
   - **Local/Regional Schemes**: Some countries have their card schemes, such as UnionPay in China, RuPay in India, or EFTPOS in Australia. These may be more cost-effective or tailored to local payment behaviors.

10. **New Developments and Innovation**: As digital payments evolve, card schemes are integrating more with financial technology (fintech). Examples include:
    - **Digital Wallets**: Schemes work with services like Apple Pay, Google Pay, and Samsung Pay, enabling payments through mobile devices without needing a physical card.
    - **Cryptocurrency Integration**: Some card schemes are exploring ways to integrate cryptocurrencies, allowing users to convert crypto to fiat currency for everyday purchases.
    - **Buy Now, Pay Later (BNPL)**: Card schemes are partnering with BNPL providers to offer alternative financing options at the point of sale.

11. **Regulation and Compliance**: Card schemes are subject to various regulations depending on the jurisdiction. This includes consumer protection laws, anti-money laundering (AML) regulations, and industry standards like the **PSD2 (Payment Services Directive 2)** in the European Union, which introduced strong customer authentication (SCA) requirements.

To fully understand **card schemes** from a technical perspective, we need to break down the different components that support the entire ecosystem of payment cards, from how transactions are initiated to how they're settled. Let's dive into the **technical architecture** and key processes behind the scenes of card schemes:

### 1. **Transaction Lifecycle in a Card Scheme**

When you use a card to make a purchase, the transaction follows a complex series of steps. These include:

#### a. **Authorization**
   - **Step 1: Transaction Initiation**: The cardholder initiates a transaction by swiping, inserting, tapping the card, or entering card details for online purchases.
   - **Step 2: Merchant Requests Authorization**: The merchant sends a request for authorization to the acquiring bank, which is the financial institution that processes card payments on behalf of the merchant.
   - **Step 3: Acquirer Sends Request to Card Network**: The acquirer routes this request to the relevant card scheme (Visa, Mastercard, etc.), which determines which issuing bank (the bank that issued the card to the cardholder) should be contacted.
   - **Step 4: Issuer Validates the Transaction**: The card issuer checks the cardholder’s account to confirm sufficient funds or credit limit, the status of the card (e.g., not blocked), and whether there are any fraud indicators. This is where fraud detection systems kick in, leveraging **machine learning** and real-time analytics.
   - **Step 5: Authorization Response**: If everything is in order, the issuer sends back an authorization response, approving or declining the transaction, along with a unique **authorization code**.
   - **Step 6: Merchant Receives Response**: The acquiring bank relays the response to the merchant, and the purchase is either approved or denied.

#### b. **Clearing**
   After the transaction is authorized, the clearing process begins. Here, the details of the transaction are sent to the card scheme (Visa, Mastercard, etc.) for further processing, and the issuing bank debits the cardholder’s account.

   - The card schemes ensure that all the necessary data, including transaction amount, merchant details, and date/time, are captured and standardized. This data will be used for settlement.

#### c. **Settlement**
   - **Funds Transfer**: In this final step, the card scheme facilitates the transfer of funds between the issuing bank and the acquiring bank. This is where the merchant gets paid for the transaction, typically minus the interchange fees.
   - The settlement process can take 1-3 business days, depending on the scheme’s rules and the agreements between banks.

### 2. **Technical Components of a Card Scheme**
Several technologies and systems come into play in ensuring that card transactions are secure, fast, and reliable. Here are some of the key technical components:

#### a. **Tokenization**
   Tokenization replaces sensitive card details (such as the card number, CVV, and expiry date) with a unique token. The token is meaningless on its own but can be mapped back to the original card information by the card scheme or payment gateway.
   
   - **Use Case**: In mobile wallets (Apple Pay, Google Pay), tokenization ensures that even if a hacker intercepts the payment data, they can't use it, because it’s a token rather than the real card number.
   
#### b. **Encryption**
   Encryption is used to secure sensitive cardholder data in transit. This ensures that if the data is intercepted while moving between the cardholder, merchant, and bank, it cannot be read without the proper decryption keys.

   - **TLS (Transport Layer Security)**: All data between merchants, payment processors, and card schemes is typically encrypted using TLS to prevent eavesdropping.

#### c. **PCI DSS (Payment Card Industry Data Security Standard)**
   PCI DSS is a set of security standards designed to ensure that all companies handling credit card information maintain a secure environment. It covers areas such as:
   - Data encryption and secure storage.
   - Regular vulnerability testing and patching.
   - Network security (firewalls, anti-virus systems).
   - Access control and multi-factor authentication (MFA).

   Merchants, processors, and financial institutions must comply with PCI DSS, as mandated by card schemes.

#### d. **EMV Chip Technology**
   EMV (Europay, Mastercard, Visa) is a global standard for cards equipped with computer chips and the technology used to authenticate chip-card transactions. Unlike magnetic stripes, EMV chips generate a unique transaction code for each payment, making it much harder to clone the card.

   - **Online Authentication**: When the transaction is initiated, the terminal communicates with the chip to create a dynamic cryptogram that authenticates the card.
   - **Fallback Mechanism**: If the chip can't be read, the terminal can fall back to reading the magnetic stripe, though this method is less secure.

#### e. **Real-Time Fraud Detection Systems**
   Card schemes leverage real-time fraud detection engines to analyze millions of transactions per second and detect potentially fraudulent transactions. These systems typically use:
   - **AI and Machine Learning**: By analyzing patterns of behavior (e.g., time of purchase, location, device used), machine learning models can identify anomalies that suggest fraud.
   - **Risk-Based Authentication (RBA)**: Some card schemes use RBA, which adjusts the security checks based on the perceived risk of the transaction.

#### f. **3D Secure (3DS)**
   3D Secure is an authentication protocol used by card schemes to enhance the security of online transactions. It adds an additional step where the cardholder is required to verify their identity, often through a one-time password (OTP) sent to their phone or by biometric authentication.

   - **3DS 2.0**: The newer version of 3D Secure (2.0) is designed to improve the user experience and support authentication on mobile devices. It uses more data points to assess the risk of the transaction and can allow low-risk transactions to go through without additional verification.

### 3. **Roles of Key Entities in Card Schemes**

#### a. **Acquiring Banks**
   The acquiring bank provides the infrastructure for the merchant to accept card payments, including payment gateways and point-of-sale (POS) terminals. Technically, they maintain APIs and integration points to interact with card networks and handle large volumes of real-time requests for transaction processing.

#### b. **Issuing Banks**
   Issuing banks provide cards to consumers and are responsible for maintaining the accounts linked to these cards. They use authorization systems to determine whether a cardholder has sufficient funds or credit available for each transaction.

   - Issuing banks also play a key role in fraud detection by monitoring cardholder activity in real-time and flagging suspicious transactions.

#### c. **Payment Gateways**
   Payment gateways are technology providers that connect merchants to acquiring banks. They are responsible for securely transmitting payment information between the merchant’s website and the acquiring bank. Gateways often offer additional features like fraud prevention tools, tokenization, and the ability to accept multiple payment methods.

#### d. **Payment Processors**
   Payment processors handle the communication between merchants, card networks, and financial institutions. They provide the backend infrastructure that ensures transactions are routed correctly and securely processed.

   - Some processors specialize in specific regions or transaction types (e.g., cross-border payments), while others offer a full suite of global payment processing services.

### 4. **Regulatory and Compliance Considerations**
   - **PSD2 (Payment Services Directive 2)**: In the European Union, PSD2 mandates **Strong Customer Authentication (SCA)**, requiring two-factor authentication for most card transactions.
   - **Anti-Money Laundering (AML)**: Card schemes and financial institutions must comply with global AML regulations to prevent illegal financial activities.
   - **GDPR**: Card schemes operating in the EU must also comply with data privacy laws, including the General Data Protection Regulation (GDPR), which requires strict management of consumer data.

### 5. **Settlement Process**
   Technically, the settlement process involves **batch processing**, where transactions are aggregated into batches and settled at the end of the business day. This process involves communication between the card scheme, acquiring bank, and issuing bank.

   - **Reconciliation**: Both merchants and acquirers receive settlement reports, which they use to reconcile the funds received with the transactions initiated.
   - **Currency Conversion**: For cross-border transactions, card schemes often facilitate real-time currency conversion using the daily exchange rates set by the scheme.

### Conclusion
Card schemes operate as a vast technical infrastructure that enables seamless, secure, and reliable payments globally. They ensure that transactions flow between merchants, acquirers, issuers, and consumers while enforcing rigorous security protocols like encryption, tokenization, and fraud detection systems. At their core, card schemes balance efficiency, security, and interoperability, allowing billions of transactions to be processed across different platforms, countries, and currencies every day.

