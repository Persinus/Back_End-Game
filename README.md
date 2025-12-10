🚀 ASTRANET – FULL ROADMAP CHUẨN HÓA (RPG + CASUAL + UNITY + IOCP + MONGODB + GUI + VUE DASHBOARD)

(FINAL LIST – dùng để làm tài liệu hoặc chia task)

⭐ MODULE 0 – Chuẩn bị nền tảng

Cấu trúc solution cho framework game RPG/Casual

Luồng xử lý Client ↔ Server cho game casual

Luồng xử lý Client ↔ Server cho game RPG

Base architecture cho Stateful Player Server

Thiết kế thư viện core: AstraNet.Core

Setup môi trường (SDK, IDE, MongoDB, Unity)

Chọn thư viện phụ trợ (Serilog, MessagePack…)

Kiến thức TCP quan trọng cho IOCP

⭐ MODULE 1 – TCP IOCP (SocketAsyncEventArgs)

Event-driven networking

IOCP scalable 10k – 100k connections

SessionModel (Idle/Active/InRoom/InCombat)

Message segmentation & sticky packet fix

SendQueue/ReceiveQueue tối ưu cho RPG/Casual

Throttle & chống spam packet

Multi-threading logic + networking

Heartbeat

Remote disconnect detection

Packet limiter & Flood protection

⭐ MODULE 2 – Serialization & Protocol

Chọn serializer: MessagePack

Packet OPCODE registry

Thiết kế PacketHeader (Opcode + Length)

Binary compression cho RPG (Skill, Combat)

Protocol versioning

Rule Set chính:

Login/Logout

PlayerInfo

Inventory

Match / Duel

Map Sync

Chat

⭐ MODULE 3 – MongoDB Layer RPG/Casual
RPG Schema

Stats

Level

EXP

Inventory

Quest

Unlocks

CASUAL Schema

Progress

Timers/Cooldowns

Rewards

Cả hai

Daily/Weekly Reset

Atomic update (findOneAndUpdate)

Caching layer (RPG-friendly)

Index cho performance

Write concern & transaction

⭐ MODULE 4 – Framework Runtime Core

Module System (Auth, Player, Quest, Match, Currency…)

EventBus RPG (OnLevelUp, OnItemReceive…)

TimeManager (Cooldown, server time)

RewardManager (Daily reward, login streak)

Data-driven Config (JSON → Hot Reload)

Sync Diff State (gửi delta)

SceneLoader (Town/Field/Dungeon)

Background Worker

Lightweight Dependency Injector

⭐ MODULE 5 – Game Logic Casual / RPG
A. CASUAL

Match Room 2–4 người

Ranking System (MMR/Elo)

Leaderboard realtime

Timer-based gameplay

Casual Boss Room (Sync đơn giản)

B. RPG

Player State (Idle → Move → Attack → Skill → Die)

Combat Calculator (damage/crit/element)

Stats growth & level formula

Inventory & Item Usage

Quest System

Dungeon Rooms (solo/party)

Monster AI (CPU-safe)

Drop Table System

Sync packet RPG (SkillCast/Damage/Buff/Debuff)

Anti-cheat (SpeedHack, Skill Spam)

⭐ MODULE 6 – Packaging Framework

AstraNet.Core.dll

AstraNet.Protocol.dll

AstraNet.RPG.dll

AstraNet.Casual.dll

AstraNet.Tools.dll

Unity Package (UPM)

Plugin Template Project cho game mới

Debug Symbols

Logging Package

⭐ MODULE 7 – Unity Client (RPG + Casual)

TCP IOCP client cho Unity

Main Thread Dispatcher

Connection State Manager (DC → Reconnect)

Bootstrap + Login scene

PlayerController (input → packet → server)

Sync Transform

Sync Combat

UI Inventory

UI Quest

UI Shop

UI Mail

Casual Mode (Room list, Ready, Match Start)

RPG HUD (HP, MP, Skill Bar)

Flow Skill: SkillCast → Damage → Sync → Animation

⭐ MODULE 8 – Admin Tools (WinForm / WPF)

Local Admin Tool (offline)

Monitor Online Players

Inspect player data

GM Commands (add exp, kick, ban…)

Room Viewer (RPG + Casual)

Log Viewer

Packet Monitor (live)

Config Editor (hot reload)

⭐ MODULE 9 – WEB DASHBOARD (VUE) LOCAL + GLOBAL
A. LOCAL WEB DASHBOARD — VUE + ASP.NET Web API

VUE 3 + Vite + Pinia

Admin Auth internal (local)

Live Metrics (WebSocket)

Player Browser

Session Heatmap (login/logoff tracking)

Server Health

Dungeon/Room Browser

Item Economy Dashboard (RPG)

Match Data Dashboard (Casual)

Local MongoDB Viewer (simple custom UI)

B. GLOBAL WEB ADMIN — VUE + ASP.NET Web API

JWT + 2FA

Multi-server support

Global Announcement

Leaderboard Dashboard

User Report/Support Tool

Multi-Region server browser

Cross-server metrics

Ban/Unban Player Center

Realtime Notifications via WebSocket

Deployment tool (update config/build version)

⭐ MODULE 10 – SUPER DEMO
DEMO CASUAL

4 người vào phòng

Sync position nhẹ

Random Map

Timer-based scoring

Leaderboard realtime

DEMO RPG

Login

Spawn Town

Di chuyển map

Skill bắn Dummy

Nhặt Item

Quái rơi loot

Damage realtime

Multi-player sync

DEMO TOOL

Winform Dashboard

Vue Global Dashboard

Edit Player Data

Restart Server

Log Viewer

Hot Reload Config

⭐ MODULE 11 – NÂNG CAO

Sharding database (RPG scale lớn)

Zone server / World server

Auth server riêng

Cross-server chat

Dedicated matchmaking server

Script Engine (Lua/C# hot reload)

⭐ MODULE 12 – RELEASE

Build Template New Game

Export Unity Sample Package (UPM)

Publish GitHub

Viết Docs

Tối ưu GC-safe

Benchmark (IOCP/MongoDB/Sync)

HelixBound