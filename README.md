# RTSP to WebRTC Streaming

This project provides a live RTSP to WebRTC streaming solution. It broadcasts video from an IP camera to a server and streams it to web clients (i.e., web browsers) using:
- WebRTC
- OpenCV
- FastAPI
- aiortc
- JavaScript

## Features

- Stream the RTSP video stream of an IP camera to web clients like Chrome
- WebRTC integration for real-time communication
- FastAPI for backend services and API endpoints
- STUN server support for NAT traversal

## Requirements

- Python 3.10+
- `pip` for package management

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/AchillesTD/RTSP2WebRTC.git
    ```

2. Create and activate a virtual environment:

    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:

    ```sh
    pip install -r requirements.txt
    ```

## Usage

1. Set the `rtsp_url` environment variable to your RTSP stream URL directly:

    ```sh
    export rtsp_url=<your_rtsp_url>  # On Windows use `set rtsp_url=<your_rtsp_url>`
    ```

   Or, create a `.env` file in the project root and add the following line:

    ```sh
    rtsp_url=<your_rtsp_url>
    ```

   Then, load the environment variables from the `.env` file before running the application:

    ```sh
    source .env  # On Windows use `set` command for each variable in the .env file
    ```

2. Run the backend server:

    ```sh
    python3 main.py
    ```

3. Open your web browser and navigate to `http://localhost:8000` to view the stream.

## Project Structure

- `main.py`: The main FastAPI application file.
- `static/client.js`: JavaScript file for handling WebRTC connections.
- `templates/index.html`: HTML template for the web client.
- `src/schemas.py`: Pydantic models for request validation.
- `requirements.txt`: List of required Python packages.

## Future Scope

I am currently trying to accomplish the same functionality using GStreamer instead of OpenCV due to its high RAM usage and overhead and well opencv uses gstreamer too so why just not eliminate the intermediary. Additionally, I need to send the same frames to multiple clients. With the current implementation of the media track, the same video gets encoded as many times as the connected clients, thus increasing the computational load significantly. I am trying to figure out how to encode the video once and send the same packets to all clients.

## Credits

This project is based on the work from [webrtc_opencv_fastapi](https://github.com/DJWOMS/webrtc_opencv_fastapi). Special thanks to the [original author](https://github.com/DJWOMS) for their contributions.
