🎯 Mục tiêu

HelixBound là framework backend game viết bằng C#, cho phép:

Tự host server (thay thế Photon SaaS)

Hỗ trợ RPG + Casual

Kiến trúc server-authoritative

Có Web Dashboard chạy local (Vue 3)

Cung cấp Unity package để client kết nối sẵn

👉 Dev chỉ tập trung làm game logic, không phải network / sync / admin.

🧱 Kiến trúc tổng thể
Unity Client
   ↓ TCP (IOCP)
HelixBound Server (C#)
   ├─ Network Core (IOCP)
   ├─ Protocol (MessagePack)
   ├─ Runtime Modules
   ├─ Game Logic (RPG / Casual)
   ├─ MongoDB Layer
   ├─ Anti-Cheat
   └─ Web API (ASP.NET)
          ↑
     Vue 3 Local Dashboard

🧩 CORE MODULES (RÚT GỌN – CHUẨN HÓA)
1️⃣ Network Core (IOCP)

TCP IOCP (SocketAsyncEventArgs)

Event-driven, scale 10k–100k connections

Session lifecycle:

Idle → Online → InRoom → InCombat

Sticky packet fix

Send/Receive Queue

Heartbeat & disconnect detect

Flood / spam packet protection

2️⃣ Protocol & Serialization

Binary protocol + MessagePack

PacketHeader: Opcode + Length

Protocol versioning

Core rules:

Login / Logout

PlayerInfo

Inventory

Match / Room

Combat / Skill

Chat

3️⃣ Database Layer (MongoDB)

RPG schema:

Stats, Level, EXP

Inventory

Quest

Dungeon progress

Casual schema:

Progress

Cooldown

Rewards

Atomic update (findOneAndUpdate)

Index & caching

Daily / Weekly reset

4️⃣ Runtime Framework

Module system:

Auth

Player

Quest

Match

Currency

EventBus (OnLevelUp, OnItemDrop…)

TimeManager (cooldown, server time)

RewardManager

Data-driven config (JSON + hot reload)

Delta sync (chỉ gửi diff)

Lightweight DI

5️⃣ Game Logic Layer
Casual

Match room (2–4 players)

Timer-based gameplay

Realtime leaderboard

Lightweight sync

RPG

Player state machine

Combat calculator

Skill / Buff / Debuff

Monster AI (CPU-safe)

Dungeon / Party

Drop table

Anti-cheat (speed hack, skill spam)

6️⃣ Packaging & SDK

HelixBound.Core.dll

HelixBound.Protocol.dll

HelixBound.RPG.dll

HelixBound.Casual.dll

HelixBound.Tools.dll

📦 Unity Package (UPM):

TCP client

Main-thread dispatcher

Connection state & reconnect

PlayerController

Transform / Combat sync

🌐 LOCAL WEB DASHBOARD (VUE 3)

Chạy local / nội bộ – không phải app C#

Tech stack

Vue 3 + Vite

Pinia

WebSocket (live data)

ASP.NET Web API backend

Tính năng

Admin auth (local)

Monitor online players

Player browser & inspect

Session heatmap

Room / Dungeon viewer

Match history (Casual)

Economy dashboard (RPG)

Server health

Log viewer

Config editor (hot reload)

Realtime metrics

👉 Mở bằng browser: http://localhost:xxxx

🧪 DEMO BUILT-IN
Casual demo

4 người vào phòng

Random map

Timer-based scoring

Realtime leaderboard

RPG demo

Login

Spawn town

Move map

Skill test

Monster drop

Multiplayer sync

Dashboard demo

Edit player data

Restart server

Hot reload config

Live monitoring

🧠 Định vị HelixBound
So sánh	HelixBound
Photon	❌ SaaS → ✔ Self-host
Mirror	❌ P2P → ✔ Server authoritative
Nakama	✔ Tương tự, thiên backend
GameLift	❌ Infra → ✔ Game framework

👉 HelixBound = Photon-like backend + Vue 3 local admin + RPG-ready core

🧾 TÓM GỌN 1 CÂU (CHUẨN)

HelixBound là framework backend game C# self-host, dùng IOCP + MongoDB, cung cấp Unity client package và Web Dashboard Vue 3 chạy local để quản trị game RPG & Casual.

Nếu bạn muốn bước tiếp theo, mình làm được:

🔹 Tách HelixBound Core vs Game Module

🔹 Định nghĩa MVP v0.1 (minimum framework)

🔹 Chia task backend / frontend / unity

🔹 Viết README + sơ đồ kiến trúc
