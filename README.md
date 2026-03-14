<div align="center">
  <h1>📡 HoboStreamer API Documentation</h1>
  <p>Public API for fetching channel data, stream status, restream links, and VODs from <a href="https://hobostreamer.com/">HoboStreamer</a>.</p>
</div>

<hr>

<h2>🔐 Authentication</h2>
<p>Currently, the HoboStreamer API is fully public. <strong>No API key or authentication is required</strong> to make requests to the endpoints listed below.</p>

<hr>

<h2>🌐 Endpoints</h2>

<h3>Get Channel Information</h3>
<p>Fetches comprehensive information about a specific channel, including profile details, current live stream data, restreaming statuses (e.g., Twitch, Kick), and past VODs.</p>

<p><strong>HTTP Request</strong></p>
<pre><code>GET https://hobostreamer.com/api/streams/channel/{channelname}</code></pre>

<h4>URL Parameters</h4>
<table>
  <thead>
    <tr>
      <th>Parameter</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>channelname</code></td>
      <td><code>string</code></td>
      <td><strong>Required.</strong> The username of the channel you want to query (e.g., <code>goosely</code>).</td>
    </tr>
  </tbody>
</table>

<h4>Example Request</h4>
<pre><code>curl -X GET https://hobostreamer.com/api/streams/channel/goosely</code></pre>

<h4>Response Structure</h4>
<p>The API returns a JSON object containing several distinct nested objects and arrays:</p>
<ul>
  <li><code>channel</code>: General profile data, panel settings, and follower counts.</li>
  <li><code>stream</code>: Information regarding the currently active stream (returns data if <code>is_live: 1</code>).</li>
  <li><code>streams</code>: An array of active streams (useful for multi-cam or concurrent broadcasts).</li>
  <li><code>rs_restream</code>: Active restreaming configurations and bot integrations.</li>
  <li><code>restream_links</code>: External platform data where the stream is being mirrored.</li>
  <li><code>vods</code>: An array of recently recorded broadcasts.</li>
</ul>

<h4>Example Response</h4>
<details>
  <summary><strong>Click to expand JSON payload</strong></summary>
  
<pre><code>{
  "channel": {
    "id": 1,
    "user_id": 1,
    "title": "goosely's Channel",
    "description": "",
    "category": "irl",
    "tags": "[]",
    "protocol": "webrtc",
    "is_nsfw": 0,
    "auto_record": 0,
    "offline_banner_url": null,
    "panels": "[]",
    "emote_sources": "{\"defaults\":true,\"custom\":true,\"ffz\":true,\"bttv\":true,\"7tv\":true}",
    "default_vod_visibility": "public",
    "default_clip_visibility": "public",
    "created_at": "2026-03-10 07:11:21",
    "updated_at": "2026-03-10 07:11:21",
    "username": "goosely",
    "display_name": "goosely",
    "avatar_url": null,
    "profile_color": "#2c78c9",
    "bio": "",
    "stream_key": "a959da5f2f6148d4b00e6717b60f2946",
    "follower_count": 6,
    "is_following": false
  },
  "stream": {
    "id": 113,
    "user_id": 1,
    "channel_id": 1,
    "title": "Desktop",
    "description": "at my girlfriend's house",
    "category": "desktop",
    "tags": "[]",
    "protocol": "webrtc",
    "is_live": 1,
    "is_nsfw": 0,
    "viewer_count": 5,
    "peak_viewers": 6,
    "follower_count": 0,
    "thumbnail_url": "/api/thumbnails/stream-113-1773453959538.jpg",
    "multi_cam": 0,
    "started_at": "2026-03-14 01:09:28",
    "ended_at": null,
    "last_heartbeat": "2026-03-14 02:05:59",
    "duration_seconds": 0,
    "created_at": "2026-03-14 01:09:28",
    "call_mode": null,
    "username": "goosely",
    "display_name": "goosely",
    "avatar_url": null,
    "profile_color": "#2c78c9",
    "endpoint": {
      "roomId": "stream-113"
    }
  },
  "streams": [
    {
      "id": 113,
      "user_id": 1,
      "channel_id": 1,
      "title": "Desktop",
      "description": "at my girlfriend's house",
      "category": "desktop",
      "tags": "[]",
      "protocol": "webrtc",
      "is_live": 1,
      "is_nsfw": 0,
      "viewer_count": 5,
      "peak_viewers": 6,
      "follower_count": 0,
      "thumbnail_url": "/api/thumbnails/stream-113-1773453959538.jpg",
      "multi_cam": 0,
      "started_at": "2026-03-14 01:09:28",
      "ended_at": null,
      "last_heartbeat": "2026-03-14 02:05:59",
      "duration_seconds": 0,
      "created_at": "2026-03-14 01:09:28",
      "call_mode": null,
      "username": "goosely",
      "display_name": "goosely",
      "avatar_url": null,
      "profile_color": "#2c78c9",
      "endpoint": {
        "roomId": "stream-113"
      }
    }
  ],
  "rs_restream": {
    "113": {
      "active": true,
      "robot_name": "Live on HoboStreamer",
      "chat_mirrored": false,
      "video_restreamed": true
    }
  },
  "restream_links": [
    {
      "platform": "twitch",
      "name": "hobostreamerdotcom",
      "channel_url": "https://twitch.tv/HoboStreamerDotCom",
      "is_live": false,
      "chat_relayed": true
    },
    {
      "platform": "kick",
      "name": "HoboStreamer",
      "channel_url": "https://kick.com/HoboStreamer?chatroom=98275805",
      "is_live": false,
      "chat_relayed": true
    }
  ],
  "vods": [
    {
      "id": 150,
      "stream_id": 111,
      "user_id": 1,
      "title": "Desktop - Empty Room",
      "description": "",
      "file_path": "/opt/hobostreamer/data/vods/vod-111-1773447879801.webm",
      "file_size": 18512751,
      "duration_seconds": 23,
      "thumbnail_url": null,
      "is_public": 1,
      "view_count": 0,
      "created_at": "2026-03-14 00:24:39",
      "is_recording": 0,
      "username": "goosely",
      "display_name": "goosely",
      "avatar_url": null,
      "stream_protocol": "webrtc"
    },
    {
      "id": 149,
      "stream_id": 111,
      "user_id": 1,
      "title": "Desktop - Empty Room",
      "description": "",
      "file_path": "/opt/hobostreamer/data/vods/vod-111-1773447872434.webm",
      "file_size": 8353706,
      "duration_seconds": 0,
      "thumbnail_url": null,
      "is_public": 1,
      "view_count": 0,
      "created_at": "2026-03-14 00:24:32",
      "is_recording": 0,
      "username": "goosely",
      "display_name": "goosely",
      "avatar_url": null,
      "stream_protocol": "webrtc"
    }
  ]
}</code></pre>

</details>

<br>
<hr>
<p align="center"><i>Powered by HoboStreamer</i></p>
