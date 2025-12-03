The AI Creative Studio

Tagline: A location-aware creative generation engine that transforms a brand’s logo and product image into 10+ hyper-personalized ad creatives with AI-generated captions in under 60 seconds.

1. The Problem (Real World Scenario)

Modern marketing teams often spend days creating slight variations of the same creative for different regions, weather conditions, seasons, and audience groups. Designers repeat the same workflow manually: adjust colors, change backgrounds, localize captions, and personalize visuals based on geography or timing.

This process is slow, unscalable, and often lacks real-world relevance. Brands miss out on contextual opportunities such as “Rainy day coffee ads in Bangalore”, “Sunny afternoon skincare ads for Chennai”, or “Weekend mall shopper ads for Gurgaon”.

2. My Solution

I built The AI Creative Studio, an auto-creative engine that uses location, weather, and contextual intelligence—similar to the signals GroundTruth leverages in advertising—to automatically generate hyper-personalized creatives.

A user uploads a brand logo and product image, and in under a minute receives a ZIP file containing:

10+ high-resolution ad creative variations

Captions aligned with weather, location, and POI context

A metadata file describing which context influenced each creative

This system allows brands to produce hyperlocal creative campaigns instantly, with no manual editing.

3. Expected End Result

Input:
Brand logo + product image

Action:
Run the generator or use the UI

Output:
A downloadable ZIP containing:

AI-generated creatives

Captions tuned to time, weather, and location

Context metadata

Example outputs:

A monsoon-themed coffee ad for Bangalore

A sunny-day fitness drink ad for Chennai

A mall-footfall evening ad for Delhi NCR

4. Technical Approach

I designed the system to combine Generative AI with real-world context signals (weather, POIs, geolocation) to make creatives meaningfully personalized.

Ingestion (User Upload)

The user provides:

Brand logo

Product image

Optional brand color palette

Context Engine (Location + Weather Intelligence)

I enrich each creative request using publicly available APIs to determine:

Current weather

Temperature and time-of-day

POIs near the target coordinates

Seasonality

This data directly influences creative prompts.

Creative Generation (Stable Diffusion / DALL-E 3)

I built a structured prompt system that blends:

Product image

Brand logo placement

Context (weather, location, POI theme)

Brand colors

Each run produces 10+ variants with different contexts.

Caption Generation (LLM: Gemini / GPT)

I feed the creative metadata to an LLM to produce:

Regionally relevant captions

CTA lines

Weather-aware messaging

Tone-consistent outputs

Guardrails

To maintain quality I implemented:

Palette enforcement based on brand colors

A “strict factual mode” to prevent hallucinated claims

Validation on caption length and relevance

Packaging

All outputs are bundled into a structured ZIP:

images/

captions.txt

metadata.json

5. Tech Stack

Language: Python 3.11

Image Generation: Stable Diffusion XL / DALL-E 3 API

Text Generation: Gemini 1.5 Pro or GPT-4.1

Context APIs: Weather API, Geolocation API, POI API

Backend Framework: FastAPI

Containerization: Docker & Docker Compose

Packaging: Pillow + zipfile

Storage: Local filesystem or S3

6. Challenges & Learnings
Challenge 1: Brand Consistency

The initial models ignored brand colors and misplaced the logo.
Fix: I implemented masked image composition and strict structured prompts.

Challenge 2: Context-Relevant Captions

Some early captions were too generic.
Fix: I switched to few-shot guided prompts and added length/style validation.

Challenge 3: Missing Context Data

Some geographic inputs had incomplete weather or POI datasets.
Fix: I added fallback logic like seasonal defaults or generalized templates.

7. How to Run
# 1. Clone Repository
git clone https://github.com/username/ai-creative-studio.git
cd ai-creative-studio

# 2. Add API Keys
export IMAGE_API_KEY="your_key_here"
export TEXT_API_KEY="your_key_here"
export WEATHER_API_KEY="your_key_here"

# 3. Build & Run Docker Container
docker-compose up --build

# 4. Test from Local UI
# Visit:
http://localhost:8000

# Upload logo + product image to generate creatives

8. Why I Chose This Problem Statement

I selected Problem Statement H-003 because it sits at the intersection of Generative AI and context-driven advertising, which is core to GroundTruth’s philosophy. GroundTruth’s competitive advantage comes from location and mobility signals; I wanted to extend that thinking into creative generation.

Most generative tools only produce visually appealing images. I wanted to build a system that produces contextually intelligent creatives—ads that adapt to the environment in which they will be shown.

This makes creative production scalable, relevant, and operationally efficient.

9. Future Enhancements (If Time Permits)

Add multilingual captions for regional campaigns

Add A/B scoring using CTR benchmarks

Detect brand fonts and auto-match typography

Add batch mode to generate 100+ creatives

Integrate footfall likelihood predictions

Provide a one-click “campaign-ready pack” (banners in 6–8 standard sizes)