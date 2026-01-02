# HN Read Tracker

A single-file web app for tracking read/unread comments in Hacker News threads. Designed to help you follow long, active discussions without losing track of what you've already read.

## Features

- **Read/Unread Tracking**: Mark individual comments or entire comment trees as read
- **Auto-collapse**: Read comments automatically collapse, keeping unread content visible
- **Smart Expansion**: Subtrees with unread comments stay expanded even if parent is read
- **Thread History**: Quick access to your 20 most recently viewed threads
- **Offline Persistence**: All read states stored in localStorage
- **Stats Display**: See how many comments you've read at a glance

## Usage

1. Open `index.html` in your browser
2. Paste a Hacker News thread URL (e.g., `https://news.ycombinator.com/item?id=12345`)
3. Click "Load Thread" or press Enter
4. Use the buttons to mark comments as read/unread

You can also pass a thread directly via query string:
```
index.html?id=12345
index.html?url=https://news.ycombinator.com/item?id=12345
```

## Controls

- **Mark Read**: Mark a single comment as read (auto-collapses)
- **Mark Unread**: Mark a comment as unread (auto-expands)
- **Mark Tree Read**: Mark a comment and all its replies as read
- **Mark All Read**: Mark every comment in the thread as read
- **[+]/[-]**: Manually collapse/expand individual comments

## Data Storage

All data is stored in browser localStorage:
- `hn-read-comments`: Read comment IDs with timestamps
- `hn-collapsed-comments`: Manually collapsed comment states
- `hn-thread-history`: Recently viewed threads (last 20)

## Technical Details

- Pure HTML/CSS/JavaScript (no dependencies)
- Uses the official [Hacker News Firebase API](https://github.com/HackerNews/API)
- Works entirely client-side
