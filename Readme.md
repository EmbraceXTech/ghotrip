# Ghotrip
This project is created to demonstrate how Purpose-Bound Money can benefit government campaigns in endorsing economic stimulation for the country. Thailand has a tourism stimulation campaign named "We Travel Together." The campaign supports Thai citizens with travel expenses (flight, hotel, and food) by covering 40% of the payment. The campaign has been successful in stimulating the travel economy in the country and raising millions in circulating money. We believe it would be even more beneficial to allow foreign travelers to join the campaign. However, the existing system is limited to Thai citizens and has a closed infrastructure that only accepts Thai Baht. To enable wider usage, we propose using a stablecoin to overcome currency issues. In this work, we have selected "GHO" as the stablecoin for the campaign due to its good price mechanism and support for seamless interactions, such as signature transfer (permit) and cross-chain transactions.

To address interoperability issues, we adhere to the Purpose-Bound Money (PBM) standard initiated by the Monetary Authority of Singapore (MAS). This standard provides a flexible interface that is easy to integrate. The stablecoin is wrapped into PBM, which contains similar logic to the We Travel Together campaign. Foreign travelers can register on the government portal and receive PBM as hotel, flight, and food discount vouchers. When they pay for hotel, flight, and food, they can attach the corresponding voucher to the payment and receive a discount. Once a registered merchant receives a voucher, it automatically unwraps into a stablecoin if the conditions are satisfied. Using PBM to implement the We Travel Together campaign unlocks the potential to accept payments from foreigners, stimulating the economy by injecting external money into the country. Moreover, using the PBM standard reduces integration costs for upcoming infrastructure, as all stakeholders conform to the same set of standards. This accelerates the scale of the campaign quickly. Importantly, all accounting is done automatically through smart contracts, reducing the burden of accounting and costs.

## How it's made
Here are the tools used to develop this project:
1. Next JS - Web frontend and API server
2. MongoDB - Simple database
3. Wagmi - Web3 connection
4. Family - Wallet connection
5. Hardhat - Smart contract development

## Frontends
This project demonstrates how different systems can work together under the same standard without exposing APIs. Hence, we implemented three different frontends that can interoperate with each other:
1. Ghovernment - the government portal to register for accepting GHOTrip vouchers. (https://github.com/EmbraceXTech/ghotrip-government-frontend)
2. GhOTA - the OTA system used to book flights and hotels. Travelers can pay with GHO and get discount benefits using GHOTrip vouchers. (https://github.com/EmbraceXTech/ghotrip-ota-frontend)
3. GhoWallet - the wallet to check balances, pay, and receive payments. (https://github.com/EmbraceXTech/ghotrip-wallet-frontend)

## Smart contracts
All frontends work on the same set of smart contracts. (https://github.com/EmbraceXTech/ghotel-contract)
1. TravelPBM - An ERC1155 token compliant with the Purpose-Bound Money standard. It wraps a stablecoin and can be transferred freely. It can be unwrapped once a payment condition is met.
2. TravelLogic - The logic contract that controls the ability to transfer and unwrap TravelPBM.
3. TravelPBMTokenManager - The manager contract that handles the TravelPBM token structure. It also manages the supply of vouchers.
4. Payment - The payment contract used to process payments between travelers, Online Travel Agency (OTA), and merchants. This contract uses the 'permit' function of GHOtoken to improve user experience when bundling vouchers with GHO tokens.
5. PBMDistributor - The contract is used to distribute all types of vouchers in one transaction.
6. GovHelper - The helper contract used in bundling whitelist and token distribution functions.

## Deployments
### Sepolia
- "GHO": "0xc4bF5CbDaBE595361438F8c6a187bDc330539c60",
- "TravelLogic": "0x6379c42E9E5c47A217EbC61570b323B3949e185B",
- "TravelPBMManger": "0x4f3492f39A528f369bf9FDC9986a7e71B921e4B6",
- "TravelPBM": "0xae3c700F9e2a46B865CeB7B3D281BAfEc1e0f915",
- "Permit2": "0x000000000022d473030f116ddee9f6b43ac78ba3",
- "Payment": "0x19f057A030F3E78fE8dE5D4d41Ff47886D569884",
- "PBMDistributor": "0xa573b820f578995a62F7242d13F59A8d46B8ee37",
- "GovHelper": "0xb09B025B2A5e1A2D8C790E6A27a3A4F49aF45b08"