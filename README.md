<div align="center">
  <h1>HoboStreamer API</h1>
  <p>The official public API documentation for <a href="https://hobostreamer.com/">HoboStreamer</a>.</p>
</div>
<img width="533" height="95" alt="11111" src="https://github.com/user-attachments/assets/d39c8e06-4229-4a63-accf-d30e2be41f92" />

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
<table>
  <thead>
    <tr>
      <th>Field</th>
      <th>Type</th>
      <th>Description</th>
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

<h2>Example Full Response</h2>
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
    },
    {
      "id": 147,
      "title": "Desktop - Empty Room",
      "duration_seconds": 6781,
      "file_size": 4120332554,
      "created_at": "2026-03-13 17:11:27"
    }
    /* ... additional VODs truncated for brevity ... */
  ]
}</code></pre>
</details>

<hr>
<p align="center">Last Updated: March 2026</p>
