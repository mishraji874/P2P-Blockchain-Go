# ⛓️ P2P Blockchain with Proof of Work in Go 🚀

Welcome to the implementation of a decentralized **Peer-to-Peer Blockchain** written in **Golang**, with a built-in **Proof of Work (PoW)** consensus algorithm. This project demonstrates the core concepts behind blockchain technology and peer-to-peer networking using [`go-libp2p`](https://github.com/libp2p/go-libp2p).

---

## 📚 What You'll Learn

- How to build a basic blockchain in Go
- Implementing Proof of Work (PoW) 🔐
- Establishing P2P connections using `go-libp2p` 🌐
- Syncing and broadcasting chains across nodes
- Decentralized decision-making via chain length

---

## 🚀 Features

- ✅ Blockchain with adjustable difficulty
- ✅ PoW mining to validate new blocks
- ✅ Real-time P2P sync and broadcast
- ✅ Read/write blockchain updates across nodes
- ✅ Command-line flag configuration for flexibility
- ✅ Minimal dependencies and under 200 lines of core logic!

---

## ⚙️ Setup Instructions

### Install the repository from the given below commands

```bash
git clone https://github.com/mishraji874/P2P-Blockchain-Go.git
cd P2P-Blockchain-Go
```

### 🔧 Prerequisites

- [Go](https://golang.org/doc/install) installed (Go 1.18 or newer recommended)

### 📦 Install Dependencies

```bash
go get github.com/davecgh/go-spew/spew
go get github.com/libp2p/go-libp2p/...
```

### 📂 Project Structure

```css
.
├── main.go
├── go.mod
├── go.sum
└── README.md
```

### 🧪 Running the App

#### Terminal 1 — Start First Node

```bash
go run main.go -l 9000 -secio
```

#### Terminal 2 — Connect a Second Node

Use the multiaddress printed in the first terminal:

```bash
go run main.go -l 9001 -d /ip4/127.0.0.1/tcp/9000/ipfs/<peer-id> -secio
```

#### Terminal 3 — Add a Third Node

```bash
go run main.go -l 9002 -d /ip4/127.0.0.1/tcp/9001/ipfs/<peer-id> -secio
```

🧠 Now all nodes are connected!

## ⛏️ How It Works

### 📦 Blockchain Structure

Each block contains:

- **Index** - Block height
- **Timestamp** - When it was created
- **BPM** - Pulse rate (our simulated transaction data)
- **Hash** - Current block's hash
- **PrevHash** - Hash of the previous block
- **Nonce** - Brute-force PoW variable
- **Difficulty** - Number of leading zeroes required in hash

### 🔐 Proof of Work (PoW)

The PoW algorithm keeps mining until a SHA256 hash starts with n leading zeroes, where `n = difficulty`.

### 🔁 P2P Syncing

- Nodes constantly broadcast their blockchain state
- Peers accept longer valid chains and update their own state
- Mutex ensures safe concurrent access to the blockchain

---

## 💡 Example Interaction

1. Input a BPM (e.g. `100`) in any terminal
2. A new block is generated using PoW and added to the blockchain
3. All peers receive and validate the new chain
4. Nodes sync automatically to the longest chain 🪢

---

## 🧠 Concepts Covered

| Concept            | Description                                          |
| ------------------ | ---------------------------------------------------- |
| **Blockchain**     | Linked list of verified data blocks                  |
| **Proof of Work**  | Mechanism to validate blocks via computational work  |
| **P2P Networking** | Nodes communicate directly without central authority |
| **Consensus**      | Accepting the longest valid chain                    |
| **Concurrency**    | Handled using Go routines and `sync.Mutex`           |

## 🛠 Improvements & Ideas

- 🧠 Add persistent storage to prevent data loss
- 💬 Implement JSON-RPC or gRPC APIs
- 🌐 Use DNS seed discovery for more scalable peer finding
- 🔐 Add stronger validation, rate limits, and DDoS protection
- 📦 Dockerize for easier deployment

---

## 📜 Commands Summary

| Command  | Description                                         |
| -------- | --------------------------------------------------- |
| `-l`     | Port to listen on (required)                        |
| `-d`     | Multiaddress of the peer to connect to              |
| `-secio` | Enable secure connection (recommended)              |
| `-seed`  | Optional seed to generate peer ID deterministically |

---

## 🙌 Credits

- Built with ❤️ in Go
- Networking powered by libp2p
- Inspired by Bitcoin’s decentralized principles
- Spew visualization with `go-spew`

---

## 📄 License

MIT License. Feel free to fork, modify, and contribute!

## 📬 Feedback

Got questions or suggestions? Feel free to open an issue or reach out! 😊

## 📬 Contact

For any inquiries or support, reach out via:

🌐 Portfolio: https://adityamishra-dev.vercel.app/

🐦 Twitter: https://x.com/mishraji874_eth

🔗 LinkedIn: https://www.linkedin.com/in/aditya-mishra-a76237226/
