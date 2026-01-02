# CLAUDE.md

## Project Overview

HN Read Tracker - a single-file web application for tracking read/unread comments in Hacker News threads.

## Architecture

Single file: `index.html` containing all HTML, CSS, and JavaScript inline.

## Key Components

### API
- Uses HN Firebase API: `https://hacker-news.firebaseio.com/v0`
- `fetchItem(id)` - fetches story or comment
- `fetchComments(ids, depth)` - recursively fetches comment trees

### State Management (localStorage)
- `hn-read-comments` - object mapping comment IDs to read timestamps
- `hn-collapsed-comments` - object mapping comment IDs to collapsed state
- `hn-thread-history` - array of {id, title, timestamp} for recent threads

### Key Functions
- `loadThread()` - main entry point, fetches and renders a thread
- `markAsRead(id)` / `markAsUnread(id)` - toggle read state
- `markTreeAsRead(id)` - marks comment and all descendants as read
- `toggleCollapse(id)` - manual collapse/expand
- `hasUnreadDescendants(comment, readComments)` - checks if subtree has unread comments

### Comment Rendering Logic
- Read comments auto-collapse (text hidden, shows preview)
- Subtrees with unread descendants stay expanded even if parent is read
- Orange left border indicates unread; faded opacity indicates read

## Styling
- HN-inspired color scheme (orange #ff6600, beige background #f6f6ef)
- Nested replies indented with left border
- Mobile-responsive with system font stack

## URL Parameters
- `?id=12345` - load thread by ID
- `?url=https://news.ycombinator.com/item?id=12345` - load by full URL
