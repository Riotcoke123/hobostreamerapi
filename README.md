Here is the complete documentation, including the new "How-to-Use" guides, consolidated into a single HTML structure for your README or website.

HTML
<div align="center">
  <h1>HoboStreamer API & Developer Tools</h1>
  <p>The official public documentation for <a href="https://hobostreamer.com/">HoboStreamer</a> and the <a href="https://dev.hobo.tools/">HoboDev</a> utility suite.</p>
</div>

<div align="center">
  <img width="533" height="95" alt="HoboStreamer Logo" src="https://github.com/user-attachments/assets/d39c8e06-4229-4a63-accf-d30e2be41f92" />
</div>

<hr>

<h2>Authentication</h2>
<p>The API is currently <strong>public</strong>. No API keys or headers are required to access public channel data.</p>

<hr>

<h2>Endpoints</h2>

<h3>Get Channel Metadata</h3>
<p>Returns the complete state of a channel, including active stream status, third-party restream links (Kick/Twitch), and a historical list of VODs.</p>

<pre><code>GET https://hobostreamer.com/api/streams/channel/{username}</code></pre>

<h4>Response Objects</h4>
<ul>
  <li><strong>channel</strong>: Profile metadata, social settings, and follower counts.</li>
  <li><strong>stream</strong>: Real-time data for the current broadcast (title, category, viewer count).</li>
  <li><strong>restream_links</strong>: Array of external platforms where the stream is currently being mirrored.</li>
  <li><strong>vods</strong>: A comprehensive history of past broadcasts including file paths and durations.</li>
</ul>

<hr>

<h2>Data Definitions</h2>
<table width="100%">
  <thead>
    <tr>
      <th align="left">Field</th>
      <th align="left">Type</th>
      <th align="left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>is_live</code></td>
      <td><code>boolean (0/1)</code></td>
      <td>Indicates if the stream is currently broadcasting.</td>
    </tr>
    <tr>
      <td><code>viewer_count</code></td>
      <td><code>integer</code></td>
      <td>Current number of active viewers on the platform.</td>
    </tr>
    <tr>
      <td><code>chat_relayed</code></td>
      <td><code>boolean</code></td>
      <td>Confirms if chat is being synced between HoboStreamer and external links.</td>
    </tr>
    <tr>
      <td><code>file_path</code></td>
      <td><code>string</code></td>
      <td>The internal server path where the VOD recording is stored.</td>
    </tr>
  </tbody>
</table>

<hr>

<h2>HoboDev: Developer & SEO Tools</h2>
<p>We provide a suite of web-based utilities for debugging, formatting, and SEO analysis at <a href="https://dev.hobo.tools/">dev.hobo.tools</a>.</p>

<h3>Tool Categories</h3>
<table width="100%">
  <thead>
    <tr>
      <th align="left">Category</th>
      <th align="left">Key Utilities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Data & Formats</strong></td>
      <td>JSON/YAML/XML/CSV/SQL Formatters, Markdown to HTML.</td>
    </tr>
    <tr>
      <td><strong>Encoding & Crypto</strong></td>
      <td>Base64, JWT Decoder, UUID Generator, SHA Hashers.</td>
    </tr>
    <tr>
      <td><strong>Time & Scheduling</strong></td>
      <td>Unix Timestamp Converter, Cron Expression Parser.</td>
    </tr>
    <tr>
      <td><strong>Code Quality</strong></td>
      <td>JS/CSS Beautifier & Minifier, Regex Tester, Diff Checker.</td>
    </tr>
    <tr>
      <td><strong>HTTP & API</strong></td>
      <td>cURL to Fetch/Python/Node converter, Webhook Inspector.</td>
    </tr>
    <tr>
      <td><strong>Frontend & SEO</strong></td>
      <td>Color Palette Converter, OpenGraph & Twitter Card Preview.</td>
    </tr>
  </tbody>
</table>

<p>Most tools are accessible via subdomains for quick access (e.g., <code>https://json.hobo.tools</code>).</p>

<hr>

<h2>Usage Guides</h2>

<h3>🛠️ HoboWebhook: Webhook Inspector</h3>
<p>Catch and visualize HTTP requests in real-time. Perfect for debugging third-party integrations (Discord, Stripe, etc.).</p>
<ol>
  <li><strong>Generate a Bin:</strong> Navigate to <a href="https://dev.hobo.tools/webhook">dev.hobo.tools/webhook</a> and click <strong>"Create Bin"</strong>.</li>
  <li><strong>Copy your URL:</strong> Use the unique endpoint provided (e.g., <code>https://api.hobo.tools/webhook/bins/.../in</code>).</li>
  <li><strong>Send a Request:</strong> Point your webhook events to that URL.</li>
  <li><strong>Inspect:</strong> The page polls automatically to display incoming <strong>Headers</strong> and <strong>Payloads</strong>.</li>
</ol>

<h3>🐚 HoboCurl: cURL Converter</h3>
<p>Translate raw cURL commands into clean code for your specific tech stack.</p>
<ul>
  <li><strong>Paste:</strong> Drop your multi-line cURL command into the input field.</li>
  <li><strong>Select Output:</strong> Choose from <strong>To Fetch</strong> (JS), <strong>To Python</strong> (Requests), <strong>To Node</strong> (HTTPS), or <strong>Parsed</strong> (JSON).</li>
  <li><strong>Run:</strong> Click "Run" to generate the code block for your project.</li>
</ul>

<hr>

<h2>Example Full API Response</h2>
<details>
  <summary><strong>View Production JSON (goosely)</strong></summary>
<pre><code>{
  "channel": {
    "id": 1,
    "username": "goosely",
    "display_name": "goosely",
    "title": "goosely's Channel",
    "category": "irl",
    "follower_count": 6,
    "stream_key": "a959da5f2f6148d4b00e6717b60f2946"
  },
  "stream": {
    "id": 114,
    "title": "Desktop",
    "is_live": 1,
    "viewer_count": 6,
    "peak_viewers": 7,
    "started_at": "2026-03-14 02:11:27"
  },
  "restream_links": [
    {
      "platform": "twitch",
      "channel_url": "https://twitch.tv/HoboStreamerDotCom",
      "chat_relayed": true
    },
    {
      "platform": "kick",
      "channel_url": "https://kick.com/HoboStreamer?chatroom=98275805",
      "chat_relayed": true
    }
  ],
  "vods": [
    {
      "id": 151,
      "title": "Desktop",
      "duration_seconds": 3665,
      "file_size": 868774690,
      "created_at": "2026-03-14 01:10:16"
    }
  ]
}</code></pre>
</details>

<hr>
<p align="center">Last Updated: March 2026</p>
