# Tiny Twitter

## Overview

This project is a simplified system design implementation of a social feed system inspired by Twitter. It focuses on high-throughput posting, timeline generation, and feed ranking at scale.

The goal is to understand how large-scale social feeds are built, especially the tradeoffs between precomputing timelines and generating them on demand.

---

## Problem Statement

Social feed systems must efficiently handle large volumes of user posts while delivering personalized timelines in real time. The system must support fast writes (posting tweets) and extremely fast reads (loading timelines), often under heavy skew where a small number of users generate most content.

This project explores how to design a simplified version of a social feed system that supports posting, following, and timeline generation.

---

## Learning Objectives

- Understand feed generation strategies (fanout-on-write vs fanout-on-read)
- Learn how timelines are constructed at scale
- Explore caching strategies for hot feeds
- Understand write-heavy vs read-heavy tradeoffs
- Learn how follower graphs impact system design
- Explore ranking and ordering strategies for feeds
- Build intuition for high-scale social platforms

---

## Core Features

### Posting System
- Create tweets/posts
- Retrieve individual posts
- Store user-generated content

### Social Graph
- Follow/unfollow users
- Maintain follower relationships
- Support basic graph traversal for feeds

### Timeline System
- Generate home timeline for users
- Support chronological or ranked feeds
- Merge posts from followed users

### Feed Delivery
- Efficient retrieval of recent posts
- Precomputed feed vs on-demand aggregation (conceptual)
- Pagination of timeline results

---

## Architecture (Conceptual)

### User Service
- Handles post creation
- Manages follow relationships

### Feed Service
- Builds and serves timelines
- Aggregates posts from followed users

### Storage Layer
- Stores posts and social graph data
- Supports fast retrieval of recent posts

### Fanout Layer (Conceptual)
- Pushes posts to followers’ feeds (fanout-on-write)
- Or computes feeds at request time (fanout-on-read)

---

## Engineering Considerations

- Handling high write volume from viral users
- Feed freshness vs computation cost tradeoffs
- Fanout explosion for users with many followers
- Cache invalidation for timelines
- Ordering consistency across distributed posts
- Scalability of social graph queries
- Hot partition problems in viral content scenarios

---

## Integration Ideas

- Distributed Systems (fanout strategies and messaging)
- Caching system (hot timeline optimization)
- Rate Limiter (posting abuse prevention)
- Message Queue (feed propagation pipeline)
- Load Testing (timeline read/write stress testing)

---

## Status

🟡 Planned
