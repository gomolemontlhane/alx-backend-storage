# ALX Backend Storage

## Overview

This repository contains comprehensive backend storage projects focused on advanced database management and caching solutions. The projects progress from advanced SQL optimization through NoSQL databases (MongoDB) to Redis-based caching systems. These foundational storage technologies are critical for building scalable, high-performance backend systems.

## Repository Structure

The repository is organized into 3 progressive projects:

### Core Projects Summary

This repository covers:

- **Advanced MySQL (0x00)** - Complex SQL queries, optimization, and database design
- **NoSQL Databases (0x01)** - MongoDB document-oriented data modeling and operations
- **Redis Caching (0x02)** - In-memory data storage, session management, and cache strategies

## Detailed Project Breakdown

### Database Projects

| Project | Directory | Technologies | Topics | Difficulty |
|---------|-----------|--------------|--------|------------|
| MySQL Advanced | 0x00-MySQL_Advanced | MySQL 5.7+ | Advanced SQL, Optimization, Indexes | Intermediate |
| NoSQL (MongoDB) | 0x01-NoSQL | MongoDB 4.0+ | BSON, Collections, Aggregation | Intermediate |
| Redis Basics | 0x02-redis_basic | Redis 6.0+ | Key-Value, Data Types, Persistence | Intermediate |

## Project Details

### 0x00 - MySQL Advanced

**Description**: Advanced MySQL database concepts and optimization techniques for production environments.

**Key Concepts**:
- Complex JOIN operations (INNER, LEFT, RIGHT, FULL)
- Subqueries and correlated queries
- Indexes and query optimization
- Stored procedures and triggers
- View creation and management
- Transaction handling and ACID properties
- Database design and normalization
- Performance tuning and explain plans

**Technology Stack**:
- MySQL 5.7 or higher
- SQL language features
- Query optimization tools
- Database administration tools

**Learning Outcomes**:
- ✓ Master advanced SQL query techniques
- ✓ Optimize database performance using indexes
- ✓ Design efficient database schemas
- ✓ Implement complex data retrieval operations
- ✓ Manage transactions and data consistency
- ✓ Create and manage views and stored procedures
- ✓ Understand query execution plans
- ✓ Implement data backup and recovery strategies

**File Structure**:
```
0x00-MySQL_Advanced/
├── README.md              # Project documentation
├── task_0.sql            # Task solutions
├── task_1.sql
├── task_2.sql
├── ...
└── test_files/           # Test data and scripts
```

**Common Tasks**:
- Writing efficient JOIN queries
- Creating indexes for optimization
- Writing stored procedures
- Analyzing query performance
- Database schema design

---

### 0x01 - NoSQL (MongoDB)

**Description**: Introduction to NoSQL database concepts using MongoDB, including document modeling and aggregation pipelines.

**Key Concepts**:
- Document-oriented data model
- BSON format and data types
- Collections and documents
- Query operators and filters
- Aggregation framework
- Indexing in MongoDB
- Replication and sharding basics
- Connection and CRUD operations
- Validation and schema design

**Technology Stack**:
- MongoDB 4.0 or higher
- MongoDB drivers (Python, Node.js)
- MongoDB tools (mongosh, Compass)
- Docker for containerization

**Learning Outcomes**:
- ✓ Understand document-oriented database concepts
- ✓ Design flexible document schemas
- ✓ Perform CRUD operations in MongoDB
- ✓ Query documents using various operators
- ✓ Use aggregation pipelines for complex queries
- ✓ Implement indexing strategies
- ✓ Handle transactions in MongoDB
- ✓ Optimize queries for performance

**File Structure**:
```
0x01-NoSQL/
├── README.md              # Project documentation
├── task_0.py             # Python/Node.js solutions
├── task_1.py
├── task_2.py
├── ...
├── dump.zip              # Sample data files
└── test_files/           # Test data and scripts
```

**Common Tasks**:
- Creating and managing collections
- Inserting and updating documents
- Querying documents with filters
- Using aggregation pipelines
- Creating indexes
- Bulk operations

---

### 0x02 - Redis Basics

**Description**: Introduction to Redis, an in-memory data structure store used for caching, session management, and real-time analytics.

**Key Concepts**:
- Redis data types (strings, lists, sets, hashes, sorted sets)
- Key-value operations
- Expiration and TTL
- Persistence mechanisms (RDB, AOF)
- Pub/Sub messaging
- Redis transactions
- Connection management
- Memory optimization
- Server administration

**Technology Stack**:
- Redis 6.0 or higher
- Redis clients (redis-py, node-redis)
- Redis CLI
- Docker for Redis containerization
- Python/Node.js for client development

**Learning Outcomes**:
- ✓ Understand Redis data structures
- ✓ Perform basic and advanced operations
- ✓ Implement caching strategies
- ✓ Manage session data with Redis
- ✓ Use pub/sub for messaging
- ✓ Configure persistence options
- ✓ Optimize memory usage
- ✓ Monitor and troubleshoot Redis

**File Structure**:
```
0x02-redis_basic/
├── README.md              # Project documentation
├── task_0.py             # Python solutions
├── task_1.py
├── task_2.py
├── ...
└── test_files/           # Test data and scripts
```

**Common Tasks**:
- Setting and getting values
- Working with lists and sets
- Implementing caches
- Session management
- Pub/Sub messaging
- Key expiration and cleanup

## Technology Stack

### Databases
- **MySQL** - Relational database for complex queries
- **MongoDB** - Document-oriented NoSQL database
- **Redis** - In-memory data structure store

### Languages & Tools
- **SQL** - Queries and database operations
- **Python** - Primary scripting language
- **Node.js** - Alternative runtime environment
- **Docker** - Containerization for services
- **Shell/Bash** - Scripting and automation

### Development Tools
- MySQL Workbench or DBeaver for database design
- MongoDB Compass for MongoDB visualization
- Redis CLI and monitoring tools
- Version control with Git

## Installation & Setup

### Prerequisites
- Docker & Docker Compose (recommended)
- Python 3.6+ or Node.js 12+
- Git for version control
- Basic understanding of databases

### Quick Start

```bash
# Clone the repository
git clone https://github.com/gomolemontlhane/alx-backend-storage.git
cd alx-backend-storage

# Setup using Docker (recommended)
docker-compose up -d

# MySQL Setup
mysql -u root -p
SOURCE 0x00-MySQL_Advanced/setup.sql;

# MongoDB Setup
mongosh
use alx_database
db.createCollection("users")

# Redis Setup
redis-cli
PING

# Run Python scripts
cd 0x00-MySQL_Advanced
python3 task_0.py

# Run Node.js scripts
node task_0.js
```

## Common Tasks & Examples

### MySQL Advanced Query Example

```sql
-- Complex JOIN with aggregation
SELECT 
    u.id, 
    u.name, 
    COUNT(o.id) as order_count,
    SUM(o.total) as total_spent
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE u.created_at > DATE_SUB(NOW(), INTERVAL 1 YEAR)
GROUP BY u.id
HAVING order_count > 0
ORDER BY total_spent DESC;

-- Creating an index for optimization
CREATE INDEX idx_user_created ON users(created_at);
```

### MongoDB Query Example

```python
from pymongo import MongoClient

client = MongoClient('mongodb://localhost:27017')
db = client['alx_database']
users = db['users']

# Insert document
users.insert_one({
    'name': 'Alice',
    'email': 'alice@example.com',
    'age': 28,
    'created_at': datetime.datetime.now()
})

# Query documents
result = users.find({'age': {'$gte': 25}}).limit(10)

# Aggregation pipeline
pipeline = [
    {'$match': {'age': {'$gte': 25}}},
    {'$group': {'_id': None, 'avg_age': {'$avg': '$age'}}}
]
result = list(users.aggregate(pipeline))
```

### Redis Example

```python
import redis

# Connect to Redis
r = redis.Redis(host='localhost', port=6379, db=0)

# String operations
r.set('username', 'alice', ex=3600)  # Expires in 1 hour
value = r.get('username')

# List operations
r.rpush('tasks', 'task1', 'task2', 'task3')
tasks = r.lrange('tasks', 0, -1)

# Set operations
r.sadd('tags', 'python', 'backend', 'database')
tags = r.smembers('tags')

# Hash operations
r.hset('user:1', mapping={'name': 'alice', 'email': 'alice@example.com'})
user_data = r.hgetall('user:1')
```

## Key Concepts by Topic

### MySQL Advanced Concepts
- **Query Optimization**: Using EXPLAIN, indexes, and query rewriting
- **Joins**: INNER, LEFT, RIGHT, FULL OUTER joins and self-joins
- **Aggregations**: GROUP BY, HAVING, window functions
- **Stored Objects**: Procedures, functions, triggers, views
- **Transactions**: ACID properties, isolation levels, lock management
- **Replication**: Master-slave architecture and data synchronization

### NoSQL/MongoDB Concepts
- **Document Model**: Flexible schema, embedded documents, arrays
- **Query Language**: Operators, filters, projection
- **Aggregation**: Pipeline stages, grouping, reshaping
- **Indexing**: Single field, compound, text, geospatial indexes
- **Transactions**: Multi-document ACID transactions
- **Sharding**: Horizontal scaling and data distribution

### Redis Concepts
- **Data Types**: Strings, lists, sets, sorted sets, hashes, streams
- **Operations**: GET/SET, PUSH/POP, ADD/REMOVE
- **Expiration**: TTL, key eviction policies
- **Persistence**: RDB snapshots, AOF logs
- **Pub/Sub**: Message broadcasting and subscription
- **Clustering**: High availability and scalability

## Resources & References

### MySQL Documentation
- [MySQL Official Documentation](https://dev.mysql.com/doc/)
- [MySQL Performance Tuning](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)
- [SQL Best Practices](https://use-the-index-luke.com/)

### MongoDB Documentation
- [MongoDB Official Documentation](https://docs.mongodb.com/)
- [MongoDB University Courses](https://university.mongodb.com/)
- [MongoDB Query Language](https://docs.mongodb.com/manual/reference/operator/query/)

### Redis Documentation
- [Redis Official Documentation](https://redis.io/documentation)
- [Redis Command Reference](https://redis.io/commands/)
- [Redis Persistence](https://redis.io/topics/persistence)

### Development Resources
- [Docker Documentation](https://docs.docker.com/)
- [Python Database APIs](https://www.python.org/dev/peps/pep-0249/)
- [Node.js Best Practices](https://nodejs.org/en/docs/guides/)

## Quick Reference: Database Comparison

| Feature | MySQL | MongoDB | Redis |
|---------|-------|---------|-------|
| Type | Relational | Document | In-Memory |
| Query Language | SQL | MongoDB Query Language | Commands |
| Schema | Fixed | Flexible | N/A |
| ACID Transactions | Full | Limited (4.0+) | Single Key |
| Scalability | Vertical | Horizontal | Horizontal |
| Use Case | Complex Queries | Flexible Data | Caching |
| Persistence | Disk-based | Disk-based | Optional |
| Speed | Medium | Medium | Very Fast |

## Troubleshooting Guide

### MySQL Issues
- **Connection Refused**: Ensure MySQL service is running
- **Syntax Error**: Check SQL version compatibility
- **Slow Queries**: Use EXPLAIN to analyze and add indexes
- **Lock Timeout**: Review transaction isolation levels

### MongoDB Issues
- **Connection Failed**: Check MongoDB service and network
- **Authentication Error**: Verify credentials and permissions
- **Slow Aggregation**: Optimize pipeline stages and indexes
- **Memory Issues**: Monitor and configure memory limits

### Redis Issues
- **Connection Timeout**: Verify Redis is running and accessible
- **Out of Memory**: Check memory limit and eviction policy
- **Slow Operations**: Monitor command latency and network
- **Persistence Issues**: Verify RDB/AOF configuration

## Contributing

This is an educational repository. If you find improvements:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Status & Difficulty

- **Repository Status**: Active Learning Project
- **Overall Difficulty**: Intermediate
- **Est. Time to Complete**: 3-6 months
- **Prerequisite Knowledge**: Basic database concepts
- **Recommended Pace**: 1 project per month

## License

This educational repository is provided as-is for learning purposes.

---

**Last Updated**: 2025
**Total Projects**: 3
**Databases Covered**: MySQL, MongoDB, Redis
