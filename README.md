# WasteWin - Waste Recycling Rewards System

## Overview

**WasteWin** is a blockchain-powered waste management and rewards system that incentivizes proper waste sorting, recycling, and community cleanup. It promotes sustainable cities and communities in line with UN SDG 11 by rewarding users with tokens for responsible waste disposal.

---

## Features

* Register users, collection stations, and waste collectors
* Deposit waste at certified stations with rewards based on type, weight, and quality
* Track user recycling streaks and environmental scores
* Station operators can manage capacity, empty loads, and track performance
* Community recycling challenges with pooled rewards
* Environmental impact tracking: CO2 saved, energy saved, water conserved, landfill diversion
* Reward distribution for deposits, challenges, and bonuses
* Admin-managed reward fund with adjustable reward rates

---

## Data Structures

* **waste-users** – Registered users with stats (waste deposited, rewards, streaks, environmental score)
* **collection-stations** – Registered waste collection stations and their capacity, type, and operators
* **waste-deposits** – Records of deposits with verification, rewards, and hashes
* **waste-collectors** – Licensed collectors/operators managing stations and routes
* **impact-records** – Environmental impact logs (CO2, energy, water, landfill diverted)
* **recycling-challenges** – Community challenges with goals and reward pools
* **reward-payments** – Record of token rewards distributed

---

## Key Functions

### User

* `register-user(user-name, location)` – Register a new recycling user
* `deposit-waste(station-id, waste-type, weight-grams, quality-grade)` – Deposit waste for rewards

### Station Management

* `register-station(station-name, location, station-type, accepted-waste-types, daily-capacity, reward-multiplier)` – Register a waste collection station
* `empty-station(station-id)` – Reset station load after collection

### Challenges

* `create-challenge(challenge-name, target-community, challenge-type, target-amount, reward-pool, duration-days)` – Launch a recycling challenge

### Read-Only

* `get-user-info(user)` – Retrieve user details
* `get-station-info(station-id)` – Get station details
* `get-deposit-info(deposit-id)` – Get waste deposit details
* `calculate-potential-reward(station-id, waste-type, weight-grams, quality-grade)` – Estimate reward before deposit
* `get-environmental-impact(user)` – View environmental impact of a user
* `get-platform-stats()` – Get platform-wide statistics

### Admin

* `fund-rewards(amount)` – Fund the global reward pool
* `update-reward-rate(waste-type, new-rate)` – Adjust reward rates (owner only)

---

## Constants

### Waste Categories

* Plastic, Paper, Glass, Metal, Organic, Electronic, Textile, Hazardous

### Reward Rates (per kg)

* Plastic: 100
* Paper: 50
* Glass: 75
* Metal: 200
* Organic: 25
* Electronic: 500
* Textile: 80
* Hazardous: 300

### Station Types

* Recycling, Composting, Electronic, Hazardous

### Limits

* Daily user limit: **100kg**
* Reward multiplier: **0.5x – 2x**

---

## Variables

* **next-station-id, next-deposit-id, next-impact-id, next-challenge-id, next-payment-id** – ID counters
* **total-users** – Total registered users
* **total-waste-processed** – Total processed waste (grams)
* **total-rewards-distributed** – Total rewards given (tokens)
* **reward-fund-balance** – Reward pool balance

---

## Error Codes

* `ERR-NOT-AUTHORIZED (1100)` – Unauthorized action
* `ERR-INVALID-AMOUNT (1101)` – Invalid weight or input
* `ERR-INSUFFICIENT-FUNDS (1102)` – Insufficient reward funds
* `ERR-USER-NOT-FOUND (1103)` – User not registered
* `ERR-ALREADY-REGISTERED (1104)` – Duplicate user registration
* `ERR-INVALID-WASTE-TYPE (1105)` – Waste type not recognized or unsupported
* `ERR-STATION-NOT-FOUND (1106)` – Collection station not found
* `ERR-INVALID-VERIFICATION (1107)` – Verification failed
* `ERR-DAILY-LIMIT-EXCEEDED (1108)` – Deposit exceeds daily limit
* `ERR-INVALID-COLLECTOR (1109)` – Invalid or inactive collector
