[README.md](https://github.com/user-attachments/files/21811430/README.md)
# Mentorship Badges - Aptos Smart Contract

A simple and efficient Move smart contract built on the Aptos blockchain that enables mentors to award digital badges to mentees, creating a verifiable record of skills and achievements.

## 🎯 Overview

The Mentorship Badges smart contract provides a decentralized way to:
- **Award Skills**: Mentors can issue badges for specific skills to mentees
- **Verify Achievements**: Badge details are stored on-chain for transparency
- **Track Progress**: Maintain a permanent record of mentorship achievements

## 🚀 Features

- **Simple & Efficient**: Clean, focused codebase (~30 lines)
- **On-Chain Storage**: All badge data is permanently stored on Aptos blockchain
- **Permissionless**: Anyone can view badge information
- **Gas Optimized**: Minimal transaction costs for badge operations

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
- [Aptos CLI](https://aptos.dev/cli-tools/aptos-cli-tools/install-cli/)
- [Git](https://git-scm.com/)
- [Python 3.7+](https://www.python.org/downloads/) (for testing)

## ⚙️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/mentorship-badges.git
cd mentorship-badges
```

### 2. Initialize Aptos Project
```bash
aptos init --profile default
```

### 3. Install Dependencies
The project uses the Aptos Framework. Dependencies are automatically managed through `Move.toml`.

## 📁 Project Structure

```
mentorship-badges/
├── sources/
│   └── mentorship_badges.move    # Main smart contract
├── Move.toml                     # Move package configuration
├── aptos.yml                     # Aptos CLI configuration
└── README.md                     # This file
```

## 🔧 Smart Contract Details

### Core Functions

#### `create_badge(mentor: &signer, mentee: address, skill: vector<u8>)`
- **Purpose**: Allows a mentor to create and award a badge to a mentee
- **Parameters**:
  - `mentor`: The signer (mentor) creating the badge
  - `mentee`: The address of the mentee receiving the badge
  - `skill`: The skill name as a byte vector
- **Access Control**: Only the mentor can create badges

#### `get_badge(mentee: address): (vector<u8>, address)`
- **Purpose**: Retrieves badge information for a specific mentee
- **Parameters**:
  - `mentee`: The address of the mentee
- **Returns**: Tuple of (skill, mentor_address)
- **Access Control**: Public read access

### Data Structures

#### `Badge`
```move
struct Badge has key, store {
    skill: vector<u8>,   // Skill name
    mentor: address,     // Mentor who issued the badge
}
```

## 🚀 Deployment

### Local Development Network
```bash
# Start local network
aptos node run-localnet

# In new terminal, deploy contract
aptos move publish --named-addresses MyModule=default
```

### Testnet Deployment
```bash
# Switch to testnet profile
aptos init --profile testnet --network testnet

# Get testnet tokens
aptos account fund-with-faucet --account default --amount 100000000 --profile testnet

# Deploy to testnet
aptos move publish --named-addresses MyModule=default --profile testnet
```

### Mainnet Deployment
```bash
# Switch to mainnet profile
aptos init --profile mainnet --network mainnet

# Deploy to mainnet (ensure you have sufficient APT)
aptos move publish --named-addresses MyModule=default --profile mainnet
```

## 📖 Usage Examples

### Awarding a Badge
```bash
# Mentor awards a "Python Programming" badge to mentee
aptos move run --function-id 'default::mentorship_badges::create_badge' \
  --args address:0x123... string:"Python Programming" \
  --profile default
```

### Retrieving Badge Information
```bash
# Get badge details for a mentee
aptos move view --function-id 'default::mentorship_badges::get_badge' \
  --args address:0x123... \
  --profile default
```

## 🧪 Testing

### Compile the Contract
```bash
aptos move compile
```

### Run Tests (if test files exist)
```bash
aptos move test
```

### Verify Contract
```bash
aptos move check
```

## 🔍 Contract Verification

After deployment, you can verify your contract on:
- **Testnet**: [Aptos Explorer Testnet](https://explorer.testnet.aptoslabs.com/)
- **Mainnet**: [Aptos Explorer](https://explorer.aptoslabs.com/)

## 📊 Gas Costs

- **create_badge**: ~0.001 APT (varies by network conditions)
- **get_badge**: Free (view function)

## 🤝 Contributing

We welcome contributions! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Contribution Guidelines
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

If you encounter any issues or have questions:
- Open an [Issue](https://github.com/yourusername/mentorship-badges/issues)
- Check [Aptos Documentation](https://aptos.dev/)
- Join [Aptos Discord](https://discord.gg/aptoslabs)

## 🙏 Acknowledgments

- [Aptos Labs](https://aptoslabs.com/) for the Move language and blockchain platform
- The Move language community for best practices and examples
- All contributors and mentors who inspired this project

## 🗺️ Roadmap

- [ ] Add badge expiration functionality
- [ ] Implement badge revocation
- [ ] Add multiple skills per badge
- [ ] Create badge metadata standards
- [ ] Build frontend interface
- [ ] Add badge verification system

---

**Built with ❤️ on Aptos Blockchain**

*Last updated: December 2024*
