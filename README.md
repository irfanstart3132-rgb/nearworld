# Nearworld
Hyperlocal marketplace: buy, sell or donate used books and other items with people near you.

## Get the APK (no Android Studio needed)
1. Create a free GitHub repo and upload this whole folder.
2. Open the repo > Actions > "Build Nearworld APK" > Run workflow.
3. When it finishes (~5 min), download the `nearworld-apk` artifact, unzip, copy app-debug.apk to your phone and install (allow "unknown sources").

## Or build locally
npm install && npx cap add android && npx cap sync android && npx cap open android

## How ranking works (www/index.html, function rank)
score = 0.45*proximity (exponential decay by distance) + 0.20*freshness + 0.15*search relevance + 0.10*donation boost + 0.10*seller rating
Distance uses the haversine formula; sellers' locations are fuzzed ~150 m for privacy.

## Next step for real multi-user use
Data currently lives on the device (localStorage). Replace the `S` storage helper and the items/reqs arrays with API calls to a backend (e.g. Supabase/Firebase + PostGIS geo queries) so neighbours see each other's posts.
