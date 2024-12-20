# Frame Vision API - example server endpoint implementation

Uses FastAPI to provide an endpoint that receives a single image as input and returns a string of text.

When used in conjunction with the [Frame Vision API mobile app](https://github.com/CitizenOneX/frame_vision_api), it's possible to prototype computer vision/AI apps for Brilliant Labs Frame with no mobile coding required (phone or Frame).

## Example Usage
* Clone this repository locally: `git clone https://github.com/CitizenOneX/frame_vision_api_impl`
* Create a Python virtual environment to keep dependencies local: `python -m venv .venv`
* Add dependencies for this project: `pip install fastapi uvicorn pillow`
* Start the server, listening on all network interfaces: `uvicorn main:app --reload --host 0.0.0.0`
* Hack away at `main.py` to perform your own vision/AI tasks
* Run the [Frame Vision API mobile app](https://github.com/CitizenOneX/frame_vision_api) and test your vision/AI pipeline live with your API results (or exceptions!) printed in front of your eyes

## Debugging in VSCode
The included `launch.json` has a configuration that should allow you to run `main.py` within VSCode and add breakpoints and step through your code when your API is being called. 
In order for VSCode to be able to run the `uvicorn` server that serves up your API code, your Python terminal in VSCode needs to have activated the `.venv/` Python environment for the project (otherwise it won't be able to find uvicorn etc.)

## Network interfaces
By default, `uvicorn` serves up your API on the `localhost` or `127.0.0.1` network interface, which is fine if the program calling your API is also running on the same computer.
If you plan to use the Frame Vision API mobile app to call your API with every photo it takes, then your API needs to be running at an address that the mobile app can reach. 
If your mobile phone is on the same network as your computer, then running uvicorn with `--host 0.0.0.0` should be enough to make the API visible to devices on your own network. (You might need to make sure your system's firewall allows it, if you have trouble connecting.)
If your mobile phone is not on the same network, it might be necessary to make the API internet-facing, so approach this (port-forwarding etc.) with the usual caution.
Alternatively, if your API is deployed to some cloud service, its endpoint should be accessible from any internet-connected mobile phone - but be aware there is no authentication/authorization built into this very simple example intended for prototying your vision/AI pipeline.
