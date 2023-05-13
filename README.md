## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000?tnxId=<YOUR_TRANSACTION_ID_GOES_HERE>) with your browser to see the result.

## Transaction status
- `success`: The payment has been received and the business wallet balances has been updated
- `pending`: Payment has not been received
- `failed`: Payment failed. This can happen for a couple of reasons. See the Ivorypay docs.
- `expired`: The transaction reached its expiration. Please see the Ivorypay docs.
- `awaiting_arrival`: Payment is `claimed` to have been made through an initial manual verification attempt where the balance of the transaction's address is still zero. See the payment verification endpoint on the docs.
- `pending_settlement`: The balance of the transaction address on the blockchain is a non-zero value, and the business wallet balances has not been updated due to pending validations. There is guarantee that transaction will be a success because the balance of the address on the blockchain (i.e the amount paid in by the sender) may be less than the expected amount.

## Transaction status
The following events occur as the state of a transaction changes or specifically when we poll the blockchain for the balance of the address associated with the transaction.

- `success`: Fired when a transaction is successful.
- `failed`: Fired when a transaction fails.
- `expired`: Fired when a transaction expires.
- `awaiting_arrival`: This is fired when the status of the transaction changes to `awaiting_arrival`. See details above.
- `pending_settlement`: Fired when the balance of the address of the transanction on the blockchain is a non-zero value. In order to confidently give value to the sender, ensure that the blockchain balance is equal to the tokens the sender is expected to send.
- `blockchain_check`: Fired after each round of blockchain check for the balance of the transaction address.
