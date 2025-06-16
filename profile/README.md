# 🚀 Monad Developer Hub

An open-source, comprehensive developer platform for the Monad blockchain ecosystem. This repository contains multiple services that work together to provide blockchain analytics, project management, and developer tools.

## 🏗️ Architecture

The Monad Developer Hub consists of four main components:

![image](https://github.com/user-attachments/assets/f6f99267-6201-469c-baf3-86732d71cec2)

#### 📦 Components

- **[frontend](./frontend/)** - Modern Next.js frontend with analytics dashboards
- **[backend](./backend/)** - Go REST API for project management and data
- **[ponder-indexer](./ponder-indexer/)** - Real-time blockchain indexer built with Ponder
- **[indexer-interface](./indexer-interface/)** - Interface service for indexed data

### Problem, Solution & Reasoning:

**1. Monad is FAST but not with my VPS:** This creates a bottleneck when I try to index Monad transactions and blocks to the database. The cost to read and write to the database is too high. The solution is to directly send all transactions via WebSocket to indexer-interface from Ponder. No read-write delay, all the data is realtime, network latency is the only limit!

**2. ENVIO is fast but doesn't allow us to listen on each block:** This doesn't align with our plan - we need to listen on each block, count each transaction, and sort them. The solution is to use Ponder for the real-time listener, and Envio to handle historical tracking of contracts, which will be used for Top Contract calculation.

**3. RPC calls are expensive *at least for me* & we want to simplify our multiple indexers to be fetched from 1 source:** Indexer-interface helps centralize the calls and data processing while reducing the use of RPC calls. It's also helpful for handling multiple clients at once without affecting our indexer performance.

**4. Network bottleneck and client rendering aesthetics:** How the indexer-interface works is it broadcasts as fast as possible on each arrival of parsed data from the indexer to all clients that subscribe to specific WebSocket events. But the server is only in one region - if it's accessed from far away, there will be delayed processing. 

This creates unaesthetic visualization; sometimes it's too fast, sometimes it's too slow. The inconsistent timing makes the transaction flow look choppy and unprofessional.

To achieve better results, we need a Dynamic Delay Function, which will queue the rendering. If there's a lot of data to render, it will shorten the delay of each transaction to display. If there are few transactions, it will lengthen the delay of each transaction to display. 

This will compensate for the network latency we experience and display beautiful dots while minimizing "silent empty rendering."

## ✨ Features

### 🔍 **Blockchain Analytics**
- Real-time transaction monitoring
- Contract usage analytics
- Gas usage tracking
- Network statistics
- MON token transfer analytics

### 📊 **Developer Dashboard**
- Project submission system
- Community project showcase
- Analytics visualization
- Transaction explorer

### 🏗️ **Infrastructure**
- High-performance blockchain indexing
- Real-time WebSocket updates
- RESTful APIs
- GraphQL interface

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- Go 1.21+
- PostgreSQL 12+
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/monad-developer-hub/monad-developer-hub.git
cd monad-developer-hub
```

### 2. Start the Blockchain Indexer
```bash
cd ponder-indexer
npm install
npm run dev
```

### 3. Start the Indexer Interface
```bash
cd indexer-interface
go mod download
go run main.go
```

### 4. Start the Backend API
```bash
cd backend
go mod download
cp env.example .env
# Configure your .env file
go run main.go
```

### 5. Start the Frontend
```bash
cd frontend
npm install
npm run dev
```

Visit `http://localhost:3000` to access the Developer Hub!

🌐 **Live Site**: [devhub.kadzu.dev](https://devhub.kadzu.dev)

## 🔧 Configuration

Each service has its own configuration requirements. See individual README files for detailed setup instructions:

- [Frontend Configuration](./frontend/README.md)
- [Backend Configuration](./backend/README.md)
- [Indexer Configuration](./ponder-indexer/README.md)
- [Interface Configuration](./indexer-interface/README.md)

## 🌐 API Endpoints

### Analytics API
```
GET  /analytics/contracts/most-used        # Top contracts by usage
GET  /analytics/wallets/top-gas           # Top gas spending wallets
GET  /analytics/mon/top-senders           # Top MON token senders
GET  /analytics/network/overview          # Network statistics
```

### Project Management API
```
POST /api/v1/submissions                  # Submit project
GET  /api/v1/submissions/:id              # Get submission status
GET  /api/v1/projects                     # List projects
```

### Real-time Data
```
WebSocket: ws://localhost:8080            # Real-time blockchain events
GraphQL:   http://localhost:42069/graphql # Query indexed data
```

## 🏃‍♂️ Development

### Environment Setup
1. **Database**: PostgreSQL for both backend and indexer
2. **Node.js**: For frontend and Ponder indexer
3. **Go**: For backend services

### Development Scripts
```bash
# Start all services in development mode
make dev-all

# Run tests
make test

# Build for production
make build
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Monad Labs** - For the innovative Monad blockchain
- **Ponder** - For the excellent indexing framework
- **Next.js & React** - For the frontend framework
- **Go & Gin** - For the backend services

## 📞 Support

- 🌐 Website: [devhub.kadzu.dev](https://devhub.kadzu.dev)
- 💬 Discord: [Join our community](https://discord.gg/monaddev)
---

**Built with ❤️ for the Monad community** 
