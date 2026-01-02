# CarbonIt Messenger

CarbonIt Messengeris an experimental decentralized, end-to-end encrypted P2P chat system built in Python.
It’s designed to demonstrate secure communication principles — including key rotation, message acknowledgment, offline queueing, and peer-to-peer transport — without relying on central servers.

Credits at CREDITS.md.

# - Vision

“Privacy should not be a privilege — it should be the foundation.”

CarbonIt Messenger is an open experiment to build an internet where communication is private, decentralized, and user-controlled.

# - Key Features

• True Peer-to-Peer (P2P):
Communicates directly between two users — no central server required.

• End-to-End Encryption (E2EE):
Messages are encrypted using per-session derived chat keys.

• Automatic Key Rotation:
Chat keys are rotated every 10 minutes or 25 messages to ensure forward secrecy.

• Offline Queueing:
If a peer is offline, messages are securely queued and retried once the connection is restored.

• Message Acknowledgement (ACK):
Each message includes timestamps and delivery confirmations for transparency.

• Secure Key Derivation:
Each chat session key is derived from a unique private–public key exchange (like Signal-style Diffie–Hellman).

# - Project Architecture
```
carbonIt/
├── network/
│   ├── carbonit_node.py         # main node logic (server + client)
│   └── run_node.bat             # launcher script
├── Keys/
│   ├── public_key_private_key/  # RSA or ECC key generation
│   ├── chat_key/
│   │   ├── derive_chat_key.py
│   │   └── rotate_chat_key.py
│   └── __init__.py
├── encryptdecrypt/
│   ├── encrypt_message.py
│   └── decrypt_message.py
└── LICENSE
```

⚙️ How to Run
1. Clone the Repository:

```git clone https://github.com/CarbonIt-Labs/carbonit-messenger.git```
```cd carbonit-messenger/network```

3. Run the Node

Run the run_node.bat file (Windows) or use:

python carbonit_node.py <username> <password> <peer_public_id_or_None> <peer_ip> <peer_port>


Example:

```python carbonit_node.py sam 1234 None 127.0.0.1 5050```

🧩 Security Design
Layer	Description
Identity	Each user generates a deterministic private–public keypair from their username and password.
Handshake	A shared session key is derived between peers using their public IDs.
Encryption	Messages use Fernet (AES-128 in CBC with HMAC) encryption.
Rotation	Chat keys are rotated automatically every 10 minutes or 25 messages for forward secrecy.
Integrity	Each message includes SHA-256 ID, timestamp (stap), and delivery acknowledgment (ack).
🧑‍💻 Authors & Credits

Developed by CarbonIt-Labs
Core Contributors:

Edwin Sam K Reju – CEO, Co-Founder & Developer

Dhruv J Prakash  - COO, Co-Founder & Developer


⚖️ License

Released under the GPL-3.0 license.
You are free to use, modify, and distribute — provided you retain proper attribution.
