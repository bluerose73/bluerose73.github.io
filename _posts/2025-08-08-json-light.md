---
title: "JSON Light: A JSON Viewer That Actually Shows Your Strings"
published: true
---

Tired of JSON viewers that turn multi-line strings into unreadable messes? I built **JSON Light** to solve exactly this problem.

## The Problem

Most JSON viewers display multi-line strings as one long line with literal `\n` characters instead of actual line breaks. This makes reading descriptions, error messages, or any formatted text incredibly frustrating.

## The Solution

[JSON Light](https://bluerose73.github.io/jsonlight/) features a simple **"View Raw" button** (R) next to string values. Click it, and your multi-line strings display with proper formatting – line breaks, indentation, and all.

### Key Features

- **Raw String Display**: Toggle between escaped and formatted text
- **JSONL Support**: Navigate JSON Lines files line by line  
- **File Format Support**: Support for JSON, JSONL, and GeoJSON files
- **Browser-Based**: No installation needed, data stays local

Perfect for API documentation, log analysis, LLM prompt engineering, and debugging where you need to actually *read* the content in your JSON.

## Try It

Visit [bluerose73.github.io/jsonlight](https://bluerose73.github.io/jsonlight/) or check out the [GitHub repo](https://github.com/bluerose73/jsonlight). It's completely free and open source.
