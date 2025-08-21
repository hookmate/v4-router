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

TBD

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
