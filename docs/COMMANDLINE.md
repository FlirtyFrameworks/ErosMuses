//REPOS

git clone https://github.com/oobabooga/text-generation-webui


//commands for stable diffusion

python launch.py --xformers --share --listen --api --enable-insecure-extension-access


commands for text gernetation

bash start_linux.sh --share --listen --extensions api


--public-api	

bash start_linux.sh --share --listen --extensions api --public-api	

bash start_linux.sh --share --listen --public-api	

//SILLY_TAVERN

bash start.sh --share --listen


SILLY TAVERN EXTRAS

python server.py --enable-modules=caption,summarize,classify --share

pip install --ignore-installed blinker Flask
pip install flask-cloudflared
pip install flask-compress
pip install flask-cors
pip install markdown
pip install tranformers
pip install webuiapi
pip install colorama
pip install transformers

FIX

sudo apt-get update
sudo apt-get install libgl1-mesa-glx


python server.py --enable-modules=caption,summarize,classify --share


EXXOTICA BETA LOGIN

WEBSITE ACCESS

https://5te7mtqx031pvn-8000.proxy.runpod.net/

ONE TIME PASSCODE SEXXCURED

TEXT GENERATION

https://dozens-advised-bridge-auctions.trycloudflare.com/

EXXXTRAS:

https://saturn-biographies-rio-vegetarian.trycloudflare.com/


STABLE DIFFUSION:

https://60dde6efd4fda9f060.gradio.live/

YOU CAN USSSSE THIS FOR ART ITS AUTOMATIC 111

SHOULD HAVE ALL FIXXXINGS

ENJOY YOUR SELF

LETS GET IT MAN



DISCORD BOT

STABLE DIFFUSION:

python launch.py --xformers --share --listen --api --enable-insecure-extension-access

TEXT GENERATION:

bash start_linux.sh --share --listen --extensions api




Modules
Name	Description
caption	Image captioning
summarize	Text summarization
classify	Text sentiment classification
sd	Stable Diffusion image generation (remote A1111 server by default)
silero-tts	Silero TTS server
chromadb	Vector storage server
talkinghead	Talking Head Sprites
edge-tts	Microsoft Edge TTS client
coqui-tts	Coqui TTS server
rvc	Real-time voice cloning
websearch	Google search using Selenium headless browser
Additional options
Flag	Description
--enable-modules	Required option. Provide a list of enabled modules.
Expects a comma-separated list of module names. See Modules
Example: --enable-modules=caption,sd
--port	Specify the port on which the application is hosted. Default: 5100
--listen	Host the app on the local network
--share	Share the app on CloudFlare tunnel
--secure	Adds API key authentication requirements. Highly recommended when paired with share!
--cpu	Run the models on the CPU instead of CUDA. Enabled by default.
--mps or --m1	Run the models on Apple Silicon. Only for M1 and M2 processors.
--cuda	Uses CUDA (GPU+VRAM) to run modules if it is available. Otherwise, falls back to using CPU.
--cuda-device	Specifies a CUDA device to use. Defaults to cuda:0 (first available GPU).
--talkinghead-gpu	Uses GPU for talkinghead (10x FPS increase in animation).
--coqui-gpu	Uses GPU for coqui TTS (if available).
--coqui-model	If provided, downloads and preloads a coqui TTS model. Default: none.
Example: tts_models/multilingual/multi-dataset/bark
--summarization-model	Load a custom summarization model.
Expects a HuggingFace model ID.
Default: Qiliang/bart-large-cnn-samsum-ChatGPT_v3
--classification-model	Load a custom sentiment classification model.
Expects a HuggingFace model ID.
Default (6 emotions): nateraw/bert-base-uncased-emotion
Other solid option is (28 emotions): joeddav/distilbert-base-uncased-go-emotions-student
For Chinese language: touch20032003/xuyuan-trial-sentiment-bert-chinese
--captioning-model	Load a custom captioning model.
Expects a HuggingFace model ID.
Default: Salesforce/blip-image-captioning-large
--embedding-model	Load a custom text embedding model.
Expects a HuggingFace model ID.
Default: sentence-transformers/all-mpnet-base-v2
--chroma-host	Specifies a host IP for a remote ChromaDB server.
--chroma-port	Specifies an HTTP port for a remote ChromaDB server.
Default: 8000
--sd-model	Load a custom Stable Diffusion image generation model.
Expects a HuggingFace model ID.
Default: ckpt/anything-v4.5-vae-swapped
Must have VAE pre-baked in PyTorch format or the output will look drab!
--sd-cpu	Force the Stable Diffusion generation pipeline to run on the CPU.
SLOW!
--sd-remote	Use a remote SD backend.
Supported APIs: sd-webui
--sd-remote-host	Specify the host of the remote SD backend
Default: 127.0.0.1
--sd-remote-port	Specify the port of the remote SD backend
Default: 7860
--sd-remote-ssl	Use SSL for the remote SD backend
Default: False
--sd-remote-auth	Specify the username:password for the remote SD backend (if required)