# Twitchtube

Twitchtube is a tool that automates the process of downloading videos from Twitch and uploading them to YouTube. It leverages the Twitch API to fetch videos, `yt-dlp` for downloading, and the YouTube Data API for uploading and managing playlists.

## Features

- **Fetch Videos from Twitch**: Retrieve videos from a specified Twitch account with customizable sorting and filtering options.
- **Download Videos**: Use `yt-dlp` to efficiently download videos locally.
- **Upload to YouTube**: Authenticate with YouTube and upload videos with proper metadata.
- **Track Processed Videos**: Maintain a log of processed videos to avoid duplicate uploads.
- **Error Handling**: Comprehensive error handling and logging for troubleshooting.

## Prerequisites

- Python 3.6+
- `yt-dlp` for downloading videos
- Google API Client Library for Python
- Twitch API credentials
- YouTube API credentials with proper OAuth scopes

## Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Twitchtube.git
   cd Twitchtube
   ```

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Twitch API Setup**:
   - Create an application in the [Twitch Developer Console](https://dev.twitch.tv/console/apps)
   - Obtain your Twitch `client_id` and `client_secret`
   - Find your Twitch user ID (numeric ID, not username)

4. **YouTube API Setup**:
   - Create a project in the [Google Cloud Console](https://console.cloud.google.com/)
   - Enable the YouTube Data API v3
   - Create OAuth credentials (OAuth 2.0 Client ID)
   - Download the `client_secrets.json` file and place it in the project root
   - Ensure your OAuth consent screen includes the following scopes:
     - `https://www.googleapis.com/auth/youtube.upload`
     - `https://www.googleapis.com/auth/youtube.readonly`
     - `https://www.googleapis.com/auth/youtube`
     - `https://www.googleapis.com/auth/youtube.force-ssl`

5. **Environment Variables**:
   - Create a `.env` file in the project root with your credentials:
     ```plaintext
     TWITCH_CLIENT_ID=your_twitch_client_id
     TWITCH_CLIENT_SECRET=your_twitch_client_secret
     TWITCH_USER_ID=your_twitch_user_id
     MAX_RESULTS=5
     TWITCH_VIDEO_PERIOD=all
     TWITCH_VIDEO_SORT=time
     YOUTUBE_CHANNEL=your_youtube_channel_id
     ```

## Usage

1. **Run the Script**:
   ```bash
   python twitchtube
   ```

2. **Authentication Process**:
   - On first run, the script will open a browser window for YouTube authentication
   - Grant the requested permissions to allow the script to upload videos
   - The access token will be displayed in the logs for debugging purposes

3. **Channel Selection**:
   - The script will list all available YouTube channels associated with your account
   - The channel ID specified in your `.env` file will be used for uploads

4. **Video Processing**:
   - The script will fetch videos from Twitch based on your configuration
   - Each video will be downloaded, uploaded to YouTube, and then removed locally
   - Processed videos are tracked in `processed_videos.log` to prevent duplicate uploads

## Configuration Options

| Environment Variable | Description | Default Value |
|----------------------|-------------|---------------|
| `TWITCH_CLIENT_ID` | Your Twitch API client ID | Required |
| `TWITCH_CLIENT_SECRET` | Your Twitch API client secret | Required |
| `TWITCH_USER_ID` | Your Twitch user ID (numeric) | Required |
| `MAX_RESULTS` | Maximum number of videos to process per run | 5 |
| `TWITCH_VIDEO_PERIOD` | Time period for fetching videos (all, day, week, month) | all |
| `TWITCH_VIDEO_SORT` | Sorting method for videos (time, trending) | time |
| `YOUTUBE_CHANNEL` | YouTube channel ID for uploads | Optional |

## Troubleshooting

### Common Issues

1. **Authentication Errors**:
   - Ensure your `client_secrets.json` file is correctly formatted and contains valid credentials
   - Check that you've granted all required permissions during the OAuth flow
   - If you encounter "insufficient authentication scopes" errors, delete any existing token files and re-authenticate

2. **Upload Failures**:
   - Verify your YouTube account has upload permissions
   - Check your API quota usage in the Google Cloud Console
   - Ensure your video files are valid and not corrupted

3. **Twitch API Issues**:
   - Confirm your Twitch API credentials are correct
   - Verify the Twitch user ID is correct (numeric ID, not username)

### Logging

The script uses Python's logging module to provide detailed information about its operation. By default, logs are displayed in the console with timestamps and log levels.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

## Acknowledgements

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) for video downloading capabilities
- [Google API Client Library for Python](https://github.com/googleapis/google-api-python-client)
- [Twitch API](https://dev.twitch.tv/docs/api/)
- [YouTube Data API](https://developers.google.com/youtube/v3)
