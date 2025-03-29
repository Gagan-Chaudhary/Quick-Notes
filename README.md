# Technical Learning Roadmap

## Phase 1: Core Project Execution (Weeks 1-12)

**Parallelize learning & implementation using:**  
1hr skill-building + 1hr project work daily

### Project 1: Generative AI Chatbot (Weeks 1-4)

**Learning Focus:**

- Week 1: LangChain pipelines & OpenAI function calling
- Week 2: RAG architecture with Pinecone/FAISS
- Week 3: Spring Boot reactive programming
- Week 4: RedisJSON optimizations

**Build Flow:**

1. Create API gateway with Spring WebFlux
2. Implement streaming responses with Server-Sent Events
3. Add conversation memory using RedisJSON
4. Deploy RAG pipeline with document chunking

**Resume Tip:** Highlight latency reduction through async I/O and cache optimizations

### Project 2: Distributed Rate Limiter (Weeks 5-8)

**Learning Focus:**

- Week 5: Redis Cell module & token bucket algo
- Week 6: Spring AOP for annotation-based rate limiting
- Week 7: Adaptive rate control (PID controllers)
- Week 8: Grafana/Prometheus monitoring

**Build Flow:**

1. Implement sliding window counter in Redis
2. Create @RateLimit annotation with Spring AOP
3. Add dynamic rate adjustment based on CPU usage
4. Build dashboard for quota visualization

**Resume Tip:** Quantify scale ("Handled X RPS with Y% accuracy")

### Project 3: Fraud Detection System (Weeks 9-12)

**Learning Focus:**

- Week 9: PyTorch Geometric (graph networks)
- Week 10: SageMaker Feature Store
- Week 11: Online ML with RiverML
- Week 12: SHAP model explainability

**Build Flow:**

1. Create synthetic transaction dataset
2. Train GNN model for anomaly detection
3. Deploy model as SageMaker endpoint
4. Build feature drift monitoring

**Resume Tip:** Show business impact ("Reduced fraud losses by X%")

## Phase 2: Advanced System Building (Weeks 13-16)

### Project 4: Load-Balanced Chat System (Weeks 13-16)

**Learning Focus:**

- Week 13: libuv event loop (Node.js)
- Week 14: Consistent hashing implementations
- Week 15: C++ coroutines (Boost.Asio)
- Week 16: QUIC protocol optimization

**Build Flow:**

1. Implement WebSocket server in Node.js
2. Add C++17 worker threads for message processing
3. Create Docker swarm cluster with overlay network
4. Load test with Locust.io

**Resume Tip:** Highlight concurrent user capacity and fault tolerance

## Parallel DSA Strategy

**Pattern Mapping:**

- Rate Limiter ➔ Sliding Window, Token Bucket
- Chat System ➔ Producer-Consumer, LRU Cache
- Fraud Detection ➔ Graph Algorithms
- AI Chatbot ➔ Trie/Prefix Trees

**Daily Practice:**

- 30 mins LeetCode (filter: FAANG)
- 30 mins System Design (Grokking course)
- Weekly Target: 5 Medium (2x DP, 2x Graphs, 1x Heap) + 1 Hard

## Skill Amplification Tactics

### Java/C++ Depth:

- Master Java 17 features (records, sealed classes)
- Explore C++23 coroutines for chat system

### Cloud Certifications:

- AWS Certified Developer (20hrs total)
- Focus on: Lambda cost optimization, SageMaker MLOps

### Architecture Patterns:

- Implement CQRS in Fraud Detection system
- Add SAGA pattern to Transaction Processor

## Resume Optimization

**Metrics First:**  
"Improved X by Y% using Z" > "Worked on Z"

**Tech Stack Grouping:**
Distributed Systems: Redis Cell, Hystrix, WebFlux AI/ML: GPT-4 Fine-tuning, TorchScript, HuggingFace Pipelines

**Open Source Leverage:**

- Contribute to LangChain (fix chatbot-related issues)
- Add Prometheus exporter to Rate Limiter project

## Interview Prep Timeline

- **Month 1-3:** Project building + DSA foundations
- **Month 4:** Behavioral stories ("Tell me about a scaling challenge")
- **Month 5:** Mock interviews (interviewing.io)
- **Month 6:** Offer negotiation (use levels.fyi data)

**Key Target Companies:** Databricks, Uber, Atlassian (strong Java + distributed systems demand)

_This plan positions you as a "T-shaped" engineer with both depth in distributed systems/AI and breadth across cloud-native development - exactly what 15LPA+ roles demand._
