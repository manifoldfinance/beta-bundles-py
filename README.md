# Beta Bundles

Python source code for submitting bundles through [OpenBidder](https://github.com/manifoldfinance/open-bidder-contracts/) beta auction.

## Installation

Manual installation is only required if you do not have nix and direnv.

1. **Clone the Repository:**
    ```bash
    git clone <repository_url>
    ```

2. **Install Poetry:**
    ```bash
    curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3
    ```

3. **Install Dependencies:**
    ```bash
    poetry install
    ```

## Configuration

### Environment variables 
Before running the script, ensure to set up the following environment variables:

- `L2_RPC`: RPC endpoint for connecting to Layer 2.
- `BETA_BUNDLE_RPC`: RPC endpoint for submitting beta bundles.
- `AUCTIONEER`: Address of the auctioneer contract.
- `SETTLEMENT`: Address of the settlement contract.
- `BIDDER`: Address of the bidder contract.
- `CALLER`: Ethereum address of the caller.
- `PRIVATE_KEY`: Private key associated with the caller's address.
- `WEI_PER_GAS`: Auction bid per gas

### Transactions bundle
Copy `bundle.example.json` to `bundle.json` fill out transaction information in any of 3 forms. 

- signed transactions (can use a tool such as [sign-eth-tx-py](https://github.com/manifoldfinance/sign-eth-tx-py))
- dictionary with `to`, `value` and `data`
- dictionary with `to`, `value`, `sig`, `args`

Note unsigned txs will be signed with env private key.

## Usage
```bash
poetry run beta_bundles_py/main.py
```

## Features

- **Event Handling:** Monitors Ethereum events for auction settlements.
- **Bundle Submission:** Submits bundles upon detecting settled auctions.
- **Transaction Signing:** Signs transactions using the provided private key.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
