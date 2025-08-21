# Uniswap V4 Swap Router

Fork of [V4 Swap Router](https://github.com/z0r0z/v4-router) from z0r0z & saucepoint. I'd highly recommend checking out their repo for additional information and instructions.

This fork makes the following **material** modifications:

- **CurrencySettler**: Implements a safe CurrencySettler which supports non-standard tokens like USDT. The original router did not support these tokens.
- **Removes LibZip**: Most L2s now implement Calldata Compression natively, which makes LibZip less useful. Not to mention that it makes reading transactions on block explorers really hard.
- **Removes Multicall**: The router already implements multi-hop swaps and Multicall does not support ETH input.
- **Solidity `0.8.30`**: Compiled using a newer compiler version and higher optimizer runs.

The fork makes the following **non-material** modifications:

- Tests are removed since they depended on the `Deployers` test implementation which is limited to Solidity `0.8.26`. However, the router has no functional changes and the test suite from the original repository passes on this version.
- Imports are standardized and a singular import scheme is used instead of duplicated remappings.
- No more submodules. Dependencies are managed as node modules via `pnpm`. This is more efficient especially since in most cases you will only need to import the interface. Importing this repo via git submodules is still fully supported.

## Deployment

| Chain            | Expected Address                           | Link                                                                                                    |
| ---------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| Ethereum         | 0xA4B6DB94b3017e2b7f17055Ded97D117ed5F551A | [Etherscan](https://etherscan.io/address/0xA4B6DB94b3017e2b7f17055Ded97D117ed5F551A)                    |
| Unichain         | 0x67C9C6050978c1582E4A633760B80CA2eff4015A | [Uniscan](https://uniscan.xyz/address/0x67C9C6050978c1582E4A633760B80CA2eff4015A)                       |
| OP Mainnet       | 0x186EAA4941DF95c6058C69FB30dfE23C2827f9Ac | [Etherscan](https://optimistic.etherscan.io/address/0x186EAA4941DF95c6058C69FB30dfE23C2827f9Ac)         |
| Base             | 0x15c40591096E938FE2A62515A7f4B8f4349D1DEE | [BaseScan](https://basescan.org/address/0x15c40591096E938FE2A62515A7f4B8f4349D1DEE)                     |
| Arbitrum One     | 0xC0077d448203c71f6b18061C2E95409b386982BE | [Arbiscan](https://arbiscan.io/address/0xC0077d448203c71f6b18061C2E95409b386982BE)                      |
| Polygon          | 0x8b318E3CcF4495108E8Db61a5814f6bAE98e1465 | [PolygonScan](https://polygonscan.com/address/0x8b318E3CcF4495108E8Db61a5814f6bAE98e1465)               |
| Blast            | 0xE8835Fff71cC8e2253C959683914f24d50Ac9699 | [BlastScan](https://blastscan.io/address/0xE8835Fff71cC8e2253C959683914f24d50Ac9699)                    |
| Zora             | 0x1770E250A9b67E44206542148ed7C5Df38235003 | [Zora Explorer](https://explorer.zora.energy/address/0x1770E250A9b67E44206542148ed7C5Df38235003)        |
| World Chain      | 0x3D9e82fb83cA3BDa838AF22d7F3964b25Df64EE7 | [WorldScan](https://worldscan.org/address/0x3D9e82fb83cA3BDa838AF22d7F3964b25Df64EE7)                   |
| Ink              | 0xC0077d448203c71f6b18061C2E95409b386982BE | [Ink Explorer](https://explorer.inkonchain.com/address/0xC0077d448203c71f6b18061C2E95409b386982BE)      |
| Soneium          | 0xC0077d448203c71f6b18061C2E95409b386982BE | [Soneium Blockscout](https://soneium.blockscout.com/address/0xC0077d448203c71f6b18061C2E95409b386982BE) |
| Avalanche        | 0x342F35aE81cd6743A4727CdD57e883C877a65aC2 | [Snowtrace](https://snowtrace.io/address/0x342F35aE81cd6743A4727CdD57e883C877a65aC2)                    |
| BNB Smart Chain  | 0x9461852Ae90c5633207283762a1b5Db337FB3F44 | [BscScan](https://bscscan.com/address/0x9461852Ae90c5633207283762a1b5Db337FB3F44)                       |
| Sepolia          | 0xf13D190e9117920c703d79B5F33732e10049b115 | [Etherscan](https://sepolia.etherscan.io/address/0xf13D190e9117920c703d79B5F33732e10049b115)            |
| Unichain Sepolia | 0x9cD2b0a732dd5e023a5539921e0FD1c30E198Dba | [Uniscan](https://sepolia.uniscan.xyz/address/0x9cD2b0a732dd5e023a5539921e0FD1c30E198Dba)               |
| Base Sepolia     | 0x71cD4Ea054F9Cb3D3BF6251A00673303411A7DD9 | [BaseScan](https://sepolia.basescan.org/address/0x71cD4Ea054F9Cb3D3BF6251A00673303411A7DD9)             |
| Arbitrum Sepolia | 0xcD8D7e10A7aA794C389d56A07d85d63E28780220 | [Arbiscan](https://sepolia.arbiscan.io/address/0xcD8D7e10A7aA794C389d56A07d85d63E28780220)              |

## Audits

No additional audits were performed beyond the ones on the original repository, however the router is functionally the same with added support for non-standard ERC20 tokens such as USDT.

## Design

The Uniswap V4 Swap Router supports the following features:

- Exact input swaps
- Exact output swaps
- Multi-hop swaps
- Native token (ETH) swaps
- Hook interactions
- Custom swap curves

## Usage

The best way to utilize the router is through the provided interface in this repo as well as in the [Hookmate](https://github.com/akshatmittal/hookmate) library which is included by default in [v4-template](https://github.com/uniswapfoundation/v4-template).

## Community Router Code Disclaimer

This community router code provided herein is offered on an “as-is” basis and has not been audited for security, reliability, or compliance with any specific standards or regulations. It may contain bugs, errors, or vulnerabilities that could lead to unintended consequences.

By utilizing this community router, you acknowledge and agree that:

- Assumption of Risk: You assume all responsibility and risks associated with its use.
- No Warranty: The authors and distributors of this code disclaim all warranties, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement.
- Limitation of Liability: In no event shall the authors or distributors be held liable for any damages or losses, including but not limited to direct, indirect, incidental, or consequential damages arising out of or in connection with the use or inability to use the code.
- Recommendation: Users are strongly encouraged to review, test, and, if necessary, audit the community router independently before deploying in any environment.

By proceeding to utilize this community router, you indicate your understanding and acceptance of this disclaimer.

## License

This code is licensed under the MIT License.
