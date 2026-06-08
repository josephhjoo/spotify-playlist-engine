# Spotify Playlist Engine
 
Generates personalized Spotify playlists using a KNN model trained on audio features. Connect your account and it finds songs that match your taste based on the acoustic properties of tracks you already like.
 
**[Live demo](https://spotify-playlist-engine.onrender.com)**
 
## How it works
 
1. You authenticate via Spotify OAuth 2.0
2. The app pulls audio features (tempo, danceability, energy, valence, acousticness) from your saved tracks
3. A KNN model finds the nearest neighbors in that feature space across a candidate song pool
4. The top matches get written back to your Spotify account as a new playlist
## Stack
 
Python, Flask, Scikit-learn, Spotipy, Spotify Web API, Render
 
## Setup
 
### 1. Create a Spotify app
 
Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard), create an app, and add `http://127.0.0.1:5000/callback` as a redirect URI.
 
### 2. Configure environment variables
 
```bash
cp .env.example .env
```
 
Fill in `.env` with your credentials:
 
- `SPOTIPY_CLIENT_ID` and `SPOTIPY_CLIENT_SECRET` — from your app dashboard
- `SPOTIPY_REDIRECT_URI` — needs to match what you set above
- `FLASK_SECRET_KEY` — recommended, any random string
- `SPOTIPY_SCOPE` — optional, defaults to `playlist-modify-public playlist-modify-private`
Then export to your shell:
 
```bash
set -a && source .env && set +a
```
 
### 3. Run
 
```bash
python app.py
```
 
Open `http://127.0.0.1:5000/index.html`.
 
