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
- GStreamer Integration: Replace OpenCV with GStreamer to reduce RAM usage and overhead, eliminating the intermediary step. This change aims to utilize GStreamer as a standalone solution for obtaining feeds and encoding.
- Multi-client Streaming: Implement a method to encode the video once and send the same packets to all clients, reducing CPU load. This will help prevent the CPU load from increasing linearly with the number of clients, as each additional client currently requires about 150-200 MB of RAM.

## To Do
- Video Frame Grid: Create a 2x2 or 4x4 video frame grid that displays different RTSP streams or feeds in each frame.
- RTSP Input: Allow users to input their RTSP links directly, rather than relying on hard-coded environment variables. This could involve creating a simple form on the web client for users to submit their RTSP URLs (then maybe I can display all those in a dropdown selection format on the webpage).

## Credits
This project is based on the work from [webrtc_opencv_fastapi](https://github.com/DJWOMS/webrtc_opencv_fastapi). Special thanks to the [original author](https://github.com/DJWOMS) for their contributions.
