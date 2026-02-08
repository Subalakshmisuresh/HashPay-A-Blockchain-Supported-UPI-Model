# HashPay: Blockchain Supported UPI Model

The HashPay project integrates blockchain technology with the existing UPI payment model to enhance transaction security, transparency, and trust. It introduces a decentralized verification mechanism that stores cryptographic proof of transactions on blockchain, preventing fake confirmations and simplifying dispute resolution.

## About

HashPay is a blockchain-supported UPI payment verification system designed to address common issues in digital payments such as fake payment screenshots, transaction disputes, and centralized dependency. Traditional UPI systems rely heavily on bank servers and application notifications, which can be manipulated or delayed. HashPay enhances the existing payment flow by generating a cryptographic hash for each successful transaction and storing it immutably on a blockchain ledger.

Rather than replacing the UPI infrastructure, HashPay functions as an additional proof layer. It ensures that transaction confirmations are tamper-proof and independently verifiable by users, merchants, and service providers. By storing only hashed transaction proof instead of full transaction details, the system maintains privacy, scalability, and efficiency.

## Features

Blockchain-based transaction proof verification

Cryptographic hash generation using SHA-256

Smart contract-based validation and storage

Prevention of fake payment confirmations

Transparent and tamper-proof transaction records

Faster dispute resolution

High scalability with lightweight blockchain storage

## Requirements
## Hardware Requirements

Processor: Intel i3 / i5 or equivalent

RAM: Minimum 4 GB (8 GB recommended)

Storage: 120 GB Hard Disk or above

Internet connection for blockchain interaction

## Software Requirements

Operating System: Windows 10 / Windows 11 / Ubuntu (64-bit)

Programming Language: JavaScript / Python

Blockchain Platform: Ethereum / Polygon Testnet

Smart Contract Language: Solidity

Backend Framework: Node.js with Express

Frontend Technologies: HTML, CSS, JavaScript

Database: MongoDB / SQLite

IDE: Visual Studio Code

Wallet: MetaMask

## System Architecture

The HashPay system architecture consists of a user interface for initiating UPI payments, a backend server for processing transactions and generating cryptographic hashes, a smart contract deployed on a blockchain network, and a verification module for validating transaction authenticity. After a transaction is completed through the UPI layer, a SHA-256 hash is generated and stored on blockchain using smart contracts. This ensures immutable proof storage and enables independent transaction verification without affecting UPI performance.

## Program 
## User Authentication & Login Module
```
<h3>Login</h3>
<input id="email" placeholder="Email">
<input id="password" type="password" placeholder="Password">
<button onclick="login()">Login</button>

<script>
function login() {
  fetch("/login", {
    method: "POST",
    headers: {"Content-Type":"application/json"},
    body: JSON.stringify({
      email: email.value,
      password: password.value
    })
  })
  .then(res => res.json())
  .then(data => alert(data.message));
}
</script>

```
## UPI Transaction Processing Code
```
<h3>Send Money</h3>
<input id="receiver" placeholder="Receiver UPI ID">
<input id="amount" placeholder="Amount">
<button onclick="pay()">Pay</button>

<script>
function pay() {
  fetch("/pay", {
    method: "POST",
    headers: {"Content-Type":"application/json"},
    body: JSON.stringify({
      receiverUPI: receiver.value,
      amount: amount.value
    })
  })
  .then(res => res.json())
  .then(data => alert(data.message));
}
</script>

```
## SHA-256 Transaction Hash Generation
```
const crypto = require("crypto");

function generateHash(txnId, sender, receiver, amount, time, status) {
  const data = txnId + sender + receiver + amount + time + status;
  return crypto.createHash("sha256").update(data).digest("hex");
}

```
## Smart Contract – Blockchain Proof Storage
```
pragma solidity ^0.8.0;

contract HashPay {
    mapping(string => string) public proofs;

    function storeProof(string memory txnId, string memory hash) public {
        proofs[txnId] = hash;
    }

    function getProof(string memory txnId) public view returns(string memory) {
        return proofs[txnId];
    }
}

```
## Transaction Verification & Hash Comparison
```
<h3>Verify Transaction</h3>
<input id="txnid" placeholder="Transaction ID">
<button onclick="verify()">Verify</button>

<script>
function verify() {
  fetch("/verify/" + txnid.value)
    .then(res => res.json())
    .then(data => alert(data.result));
}
</script>

```

## Output
Output 1 – Home and Payment Interface
Displays quick actions such as QR scanning, UPI ID payment, bank transfer, and bill payment, providing a user-friendly UPI-like interface integrated with blockchain-backed verification.
![1](https://github.com/user-attachments/assets/9c68e768-a990-47ae-9dba-0f51355f4abe)


Output 2 – Transaction and User Dashboard
Shows registered users, wallet addresses, transaction history, timestamps, and blockchain confirmation details, ensuring transparency and traceability.
![2](https://github.com/user-attachments/assets/8f9841a3-b902-47e1-9ffd-876fee2563d2)


Output 3 – Blockchain Confirmation
Confirms successful storage of transaction proof on blockchain via wallet confirmation, ensuring payment authenticity and immutability.
![3](https://github.com/user-attachments/assets/20fef888-a14b-49a4-a230-33306c2a2d81)


## Results and Impact

The HashPay system significantly improves trust and security in digital payments by eliminating fake payment confirmations and reducing dependency on centralized verification mechanisms. By combining UPI with blockchain-based proof storage, the system ensures tamper-proof transaction records while preserving user privacy. HashPay also simplifies dispute resolution and enhances transparency, making it a reliable foundation for future secure digital payment systems.

This project demonstrates the practical application of blockchain technology in financial systems and contributes to the development of secure, scalable, and trustworthy payment verification solutions.

## Articles Published / References

Y. Yuan et al., “Blockchain-Based Digital Payment Systems: A Survey,” IEEE Access, vol. 8, 2020.

S. Kumar et al., “Blockchain-Enabled Fraud Prevention in Digital Payment Systems,” IEEE Access, vol. 10, 2022.

A. Singh and K. Chatterjee, “Blockchain-Based Digital Payment Verification Model,” Journal of King Saud University – CIS, 2022.

R. Malhotra and P. Verma, “Secure Blockchain-Based Payment Verification Using Cryptographic Hashing,” IEEE Access, 2024.
