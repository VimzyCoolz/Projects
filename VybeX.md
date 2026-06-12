Here is a clean, plain-text summary of the VybeX blueprint. I have removed all tables, complex formatting, blocks, and symbols so you can copy and paste the entire text easily without any formatting issues.
APP IDENTITY AND PRIVACY
The app is named VybeX. The main action or verb is to Vybe, as in Let us Vybe on VX. The shorthand for the app and its features is VX.
Users sign up using an Email and a Username instead of a phone number.
The app uses Asymmetrical Privacy. If a user searches for someone by their username, the phone number and email remain completely hidden. However, if a user syncs their phone contacts and matches with a friend who is already on the app, the friend's phone number is shown because the user already has it in their physical phone book.
To keep this privacy-first contact sync secure, phone numbers and emails are hashed using SHA-256 directly on the user's phone before hitting the network. The server only returns matches for accounts that already exist and does not keep unmatched data.
THE SPAM GATE AND BADGES
To prevent stranger spam, typing a random username into the search bar only allows a user to send up to 3 introductory messages. The chat input field then locks until the recipient accepts the request.
Users in the search list and chat menus get clear visual text badges. A Contact badge shows if they are a real-world friend from the phone book. A Pending badge displays how many of the 3 introductory messages have been sent to a stranger.
THE THE FOUR-TAB LAYOUT
The app interface is split into four distinct sections:
 1. VX Chats for private one-on-one messaging.
 2. VX Groups and Communities for multi-user group chats and large announcement channels.
 3. VX Status for 24-hour disappearing text, photo, or video stories.
 4. Menu for profile management, privacy toggles, and backup settings.
A single Global Search bar sits at the top of the app, allowing users to search across contacts, public groups, status updates, and local message history all from one place.
REAL-TIME INFRASTRUCTURE
Messages are not permanently stored on a cloud database server. Instead, VybeX uses WebSockets to create an open, fast pipeline between active users. Messages travel from phone to phone in milliseconds, and the server drops them from memory instantly upon delivery.
The real chat database lives directly on the user's phone storage using a local database format like SQLite.
If a user is offline when a message is sent, the server holds the encrypted text in a temporary Offline Queue table. The moment that user reconnects, the messages are pushed to their device and immediately wiped from the server database.
THE STORAGE HACK AND BACKUPS
To keep cloud server costs at zero dollars, all heavy files are offloaded to Telegram using a dedicated backend bot and a private channel.
For media uploads, every photo, video, or voice note sent in a chat is uploaded directly to the Telegram channel as an individual message. The server saves only the unique Telegram file_id in the main database to stream it to the recipient, deleting the media from the server disk instantly. For VX Status, the media is deleted from Telegram automatically after 24 hours.
For backups, the app offers a Free Manual Backup tier and a Premium Pro Auto Backup tier. The Pro version runs an In-App Lifecycle Loop, which triggers a silent, automatic backup upload while the user is actively using or closing the app, avoiding restrictive mobile operating system background blocks.
The chat history is compressed on the phone into a lightweight JSON GZIP file. When the server uploads this backup file to Telegram, it records the message ID. Every time a user creates a new backup, the server tells the Telegram bot to delete the previous backup message. This keeps the Telegram channel clean, ensuring it holds exactly one file per active user.
