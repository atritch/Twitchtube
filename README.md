# Twitchtube

Twitchtube is a tool that automates the process of downloading videos from Twitch and uploading them to YouTube. It leverages the Twitch API to fetch videos, `yt-dlp` for downloading, and the YouTube Data API for uploading and managing playlists.

## Features

- **Fetch Videos from Twitch**: Retrieve videos from a specified Twitch account.
- **Download Videos**: Use `yt-dlp` to download videos locally.
- **Upload to YouTube**: Authenticate with YouTube and upload videos.
- **Manage Playlists**: Automatically create or update playlists on YouTube based on Twitch collections.
- **Enhanced Metadata Processing**: Automatically copy metadata such as title and description from Twitch videos to YouTube uploads.

## Prerequisites

- Python 3.x
- `yt-dlp` for downloading videos
- Google API Client Library for Python
- Twitch API credentials
- YouTube API credentials

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
   - Obtain your Twitch `client_id` and `client_secret` from the [Twitch Developer Portal](https://dev.twitch.tv/console/apps).

4. **YouTube API Setup**:
   - Create a project in the [Google Developers Console](https://console.developers.google.com/).
   - Enable the YouTube Data API v3.
   - Download the `client_secrets.json` file and place it in the project root.

5. **Environment Variables**:
   - Create a `.env` file in the project root with your credentials:
     ```plaintext
     TWITCH_CLIENT_ID=your_twitch_client_id
     TWITCH_CLIENT_SECRET=your_twitch_client_secret
     TWITCH_USER_ID=your_twitch_user_id
     YOUTUBE_CLIENT_SECRETS=client_secrets.json
     ```

## Usage

1. **Configure Your Credentials**:
   - Ensure your `.env` file is correctly set up with your Twitch and YouTube credentials.

2. **Run the Script**:
   ```bash
   python twitchtube.py
   ```

3. **Follow the Console Prompts**:
   - Authenticate with YouTube when prompted.
   - The script will download videos from Twitch and upload them to YouTube, organizing them into playlists and copying over metadata.

## Notes

- Ensure you have sufficient permissions and quota for the YouTube Data API.
- The script currently processes a maximum of 5 videos per run, but this can be adjusted in the `main()` function.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

## Contact

For any questions or issues, please open an issue on the GitHub repository or contact the maintainer at [your-email@example.com].
