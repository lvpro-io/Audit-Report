# Audit-Report

Following the recommendation by the EAN exchange audit, the La Vitesse multi-signatory committee devided to immediately implement the changes according to the recommendation:
Extracts of the reports are as follows:

CRITICAL ISSUES (critical, high severity): 0 
Bugs and vulnerabilities that enable theft of funds, lock access to funds without
possibility to restore it, or lead to any other loss of funds to be transferred to any
party; high priority unacceptable bugs for deployment at mainnet; critical
warnings for owners, customers or investors.

ERRORS, BUGS AND WARNINGS (medium, low severity): 0 
Bugs that can trigger a contract failure, with further recovery only possible
through manual modification of the contract state or contract replacement
altogether; Lack of necessary security precautions; other warnings for owners and users
OPTIMIZATION
Possibilities to decrease cost of transactions and data storage of SmartContracts.

NOTES AND RECOMMENDATIONS (very low severity): 3 
Tips and tricks, improvements, all other issues and recommendations, as well as
errors that do not affect the functionality of the Smart-Contract.

Conclusion:
The La-Vyf smart-contract was found no vulnerabilities and no backdoors. The
code was manually reviewed for all commonly known and more specific
vulnerabilities. Therefore, La-Vyf smart contract is safe for use in the main
network.

Recommendations - Optimization possibilities
1. Recording statistical parameters in the blockchain (very low severity):
List of statistical parameters that also increase the cost of transactions and increase
the amount of data stored in the blockchain:
uint256 public totalUsers; uint256 public
totalInvested; uint256 uint256
Recommendation: use events and log this information instead of writing it
to the blockchain.
Note: this comment doesn't affect the main functionality of the smart-contract.

2. Deposits and Withdrawals:
Market parameters that increase the cost of transactions affecting the user
functionality and user benefits is strongly encouraged.
Recommendation:
i. upgrade acceptance of deposits to both USDT-ERC20 and USDTTRC20.
ii. upgrade withdrawals to USDT-TRC20
Note: this comment doesn't affect the main functionality of the smart-contract.

3. Cycles on parallel deposits (very low severity):
Inthewithdraw, getUserReturns, getUserAvailable, getUserTotalDeposits, and get
UserTotalWithdrawn functions, cycles unrestrictedly grow as the number of
deposits increases. If you create a large number of parallel deposits from a
single wallet, this can lead to an excessive increase in the transaction cost and
incorrect display and processing of information.
Note: this comment is only relevant for a certain user, if he creates an excessive
number of deposits.


Independent description of the smart-contract functionality
The La-Vyf contract provides the opportunity to invest any amount in USDT (from and in multiples
of 100 USDT) in the contract and gets a 5 % return on investment.
You can create a Deposit by calling the “invest” function and attaching the required amount of
USDT to the transaction (from 100 USDT inclusive).
Each subsequent Deposit is kept separately in the contract, in order to maintain the payment
amount for each Deposit.
The percentage on the following factors:
- Withdrawals of balance are available at any time
- Withdrawal by the user is performed by calling the “withdraw” function from the address the
Deposit was made
All accruals are summed up and available for withdrawal at any time, i.e. it does not matter at
what point the user decides to withdraw the dividends.
Affiliates Commission:
- Ten-level affiliate program: in the “invest” function, you can specify the address of the upwards
affiliates.
- As a result, the upwards affiliates of up to ten-level with deposits will get opportunity to withdraw
equivalent of 10% of the investor’s Deposit returns.

The contract contains 11 statistical functions that do not require sendingtransactions:
1. getContractBalance – smart contract balance (with decimals, for USDT – 2 characters).
2. getUserReturns – the current amount of returns available to withdraw.
3. getUserCheckpoint – the date of the last withdrawal in UNIX time.
4. getUserReferrer – the user’s referrer.
5. getUserAffiliateBonus – available affiliate bonuses for withdrawal.
6. getUserAvailable – total available amount to withdraw (deposits + returns + bonuses).
7. isActive – whether the user has active deposits.
8. getUserDepositInfo – information about the user’s specified Deposit (the sequential number
of the Deposit starting from 0).
9. getUserAmountOfDeposits – the number of user deposits.
10.getUserTotalDeposits – the sum of each deposits of the user.
11.getUserTotalWithdrawn – user amount withdrawn (deposits + returns + bonuses).
