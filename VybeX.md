Core Concept & User Discovery
​The Identity: Users sign up with an Email and Username rather than a phone number.
​Asymmetrical Privacy: * If a user searches for someone via Username Search, the recipient's phone number and email remain completely hidden.
​If a user syncs their phone contacts and matches with an existing user, the app exposes their phone number because they already have it in their real-world directory.
​The Hashing Loop: To protect user privacy during contact syncs, phone numbers (normalized to E.164) and emails are hashed using SHA-256 on the device before being sent to the server for matching.
​Spam & Interaction Control
​The 3-Message Rule: To prevent stranger spam, typing a username into the search bar only allows a user to send up to 3 introductory messages. The text input locks until the recipient accepts the connection request.
​Visual Badges: Users in search results and chat lists feature explicit UI states:
​[ 👤 Contact ] for verified real-world contacts.
​[ ⏳ Pending: X/3 ] for unaccepted stranger requests.
​Real-Time Infrastructure & Messaging
​Zero-Server Storage for Messages: The app mimics WhatsApp by utilizing WebSockets for instant, real-time message delivery.
​Local Databases: Active chat history is saved directly onto the user's physical device storage using a local database (like SQLite).
​The Offline Queue: Messages are only saved to the server's cloud database if a recipient is offline. The moment they connect, the server delivers the pending messages and immediately wipes them from the server disk.
​The Monetization & Backup Hack
​The Freemium Model: * Free Tier: Users can perform manual chat backups.
​Pro Tier: Automated background backups trigger seamlessly while the app is active (on launch or when minimized) using an In-App Lifecycle Loop rather than restricted OS background tasks.
​The Telegram Storage Hack: To keep server costs down, backups are compiled into compressed JSON files (.json.gz) and sent by a dedicated bot to a private Telegram channel.
​Automatic Clean-up: The server keeps track of Telegram message_ids in a central database. When a user runs a new backup, the server tells the Telegram bot to delete the previous backup message, ensuring the channel only holds exactly one file per user.
