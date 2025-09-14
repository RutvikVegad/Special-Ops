# Special-Ops Database System

A comprehensive PostgreSQL database system designed for managing multiplayer gaming data, specifically modeled after tactical shooter games like Call of Duty Mobile. This project includes complete database schema, sample data, and query examples for managing players, clans, teams, matches, weapons, and game statistics.

## 🎮 Project Overview

The Special-Ops database system simulates a complete gaming ecosystem with:
- Player Management: User profiles, stats, customization, and loadouts
- Clan System: Organized groups with leaderboards and war streaks  
- Team Organization: Squad-based matchmaking and tournaments
- Match Tracking: Game sessions with different modes and maps
- Weapon Arsenal: Detailed weapon stats, attachments, and player usage
- Statistical Analysis: Comprehensive performance metrics and analytics

## 📊 Database Schema

### Core Entities

| Table | Purpose | Key Features |
|-------|---------|--------------|
| `Player` | User profiles and basic info | Username, email, rank, level, skills, availability |
| `Player_stats` | Performance metrics | Kills, deaths, wins, matches played, score |
| `Clans` | Group management | Leader, trophies, war streaks, leaderboard rankings |
| `Teams` | Squad organization | Team names and competitive scores |
| `Matches` | Game session tracking | Game modes, timing, map selection |
| `Maps` | Battle environments | Map types, sizes, and configurations |
| `Weapon` | Arsenal management | Damage, accuracy, fire rate, mobility stats |
| `Load_out` | Player configurations | Weapon setups, perks, tactical equipment |

### Relationship Structure

- Players belong to **Clans** and **Teams**
- Teams participate in **Matches** on specific **Maps**
- Players own **Weapons** with different mastery levels
- Each player can configure multiple **Load-outs**
- Comprehensive **Player_stats** track all performance metrics

## 🚀 Quick Start

### Prerequisites
- Database client (pgAdmin, or similar)
- Basic SQL knowledge

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/RutvikVegad/Special-Ops.git
   cd Special-Ops
   ```

2. **Create the database schema**
   ```sql
   -- Connect to PostgreSQL and create schema
   CREATE SCHEMA t207;
   SET search_path TO t207;
   
   -- Execute DDL script
   \i DDL_script.txt
   ```

3. **Load sample data**
   ```sql
   -- Populate tables with sample data
   \i Insertion_script.txt
   ```

4. **Test with sample queries**
   ```sql
   -- Run example queries
   \i Sample_Queries.txt
   ```

## 📁 File Structure

```
Special-Ops/
├── DDL_script.txt              # Database schema definition
├── Insertion_script.txt        # Sample data insertion
├── Sample_Queries.txt          # Example SQL queries  
├── Functional Dependencies.pdf # Database design analysis
├── T207_special_ops.pdf        # Project documentation
├── special_ops_er_diagram.png  # Entity-Relationship diagram
├── special_ops_relational_schema.png # Database schema visualization
└── README.md                   # This file
```

## 🔍 Key Features

### Player Management
- **Comprehensive Profiles**: Username, email, password, rank progression
- **Skill Tracking**: Specialized abilities (Sniper, Medic, Engineer, etc.)
- **Availability Status**: Online/offline tracking with last seen timestamps
- **Customization System**: Skins, camos, backpacks, vehicle modifications

### Statistical Analysis
- **Performance Metrics**: Kill/death ratios, win rates, match statistics
- **Asset Management**: In-game currency and resource tracking
- **Leaderboards**: Clan rankings and individual player standings
- **Progress Tracking**: Level progression and achievement systems

### Weapon System
- **Detailed Stats**: Fire rate, damage, accuracy, range, control, mobility
- **Arsenal Variety**: Assault rifles, sniper rifles, SMGs, shotguns, pistols
- **Progression System**: Weapon mastery levels and unlock tracking
- **Attachment System**: Scopes, grips, barrels, and other modifications

### Match Management
- **Game Modes**: Team Deathmatch, Domination, Search & Destroy, Free-for-All
- **Map Variety**: Different sizes (Small, Medium, Large) and types
- **Session Tracking**: Start/end times, participating teams, match outcomes
- **Tournament Support**: Team-based competitions with scoring systems

## 📈 Sample Queries

The project includes 30+ sample queries demonstrating:

```sql
-- Top performing clans
SELECT * FROM Clans ORDER BY Trophies DESC LIMIT 10;

-- Player kill leaderboards  
SELECT * FROM Player_stats ORDER BY Kills DESC LIMIT 10;

-- Most popular weapons
SELECT Weapon_name, COUNT(*) AS Usage_Count 
FROM Has JOIN Weapon USING(Weapon_id) 
GROUP BY Weapon_name ORDER BY Usage_Count DESC;

-- Active players by clan
SELECT Player.Username, Clans.Clan_name 
FROM Player JOIN Clans ON Player.Clan_id = Clans.Clan_id 
WHERE Avail_status = TRUE;
```

## 🎯 Use Cases

### Gaming Analytics
- **Player Behavior Analysis**: Track engagement patterns and preferences
- **Balance Optimization**: Weapon usage statistics for game balancing
- **Matchmaking Intelligence**: Skill-based pairing algorithms
- **Clan Management**: Community building and competition tracking

### Business Intelligence
- **User Retention Metrics**: Activity tracking and engagement analysis
- **Revenue Analytics**: Asset distribution and monetization insights
- **Performance Optimization**: Database query optimization for real-time gaming
- **Competitive Analysis**: Tournament statistics and leaderboard management

## 🔧 Technical Specifications

- **Database**: PostgreSQL with schema `t207`
- **Data Volume**: 40+ players, 50+ clans, 140+ teams, 50+ weapons
- **Referential Integrity**: Comprehensive foreign key relationships
- **Query Optimization**: Indexed columns for performance
- **Scalability**: Designed for thousands of concurrent players

## 📋 Database Design

### Functional Dependencies
The system maintains proper normalization through:
- **Player → Stats**: One-to-one relationship for performance data
- **Clan → Players**: One-to-many clan membership
- **Team → Matches**: Many-to-many through participation table
- **Weapon → Players**: Many-to-many with mastery levels

### Entity Relationships
- Strong entity relationships with proper cascade handling
- Comprehensive constraint management for data integrity
- Optimized indexing strategy for gaming workloads

### Development Guidelines
- Follow PostgreSQL best practices
- Maintain referential integrity
- Document all schema changes
- Include test data for new features
- Optimize queries for performance

## 🎖️ Acknowledgments

- Database design inspired by modern tactical shooter games
- Built for academic and learning purposes
- Optimized for PostgreSQL environments
- Sample data represents realistic gaming scenarios

---

