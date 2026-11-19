# SamScene Studio

The complete SamScene spatial creative studio, including SamSpeak narration and storyboard tools, environment and material editors, procedural subjects, asset import, camera direction, and project persistence.

This revision incorporates the working studio from [`SamPrimeaux/samscenev2`](https://github.com/SamPrimeaux/samscenev2) at `c7fbadb` into the existing [`SamPrimeaux/SamSpeaks`](https://github.com/SamPrimeaux/SamSpeaks) project. Existing voices, scene presets, source media and editing flows are preserved.

## Run locally

Requires Node.js 24 (the server uses native `node:sqlite`).

```sh
npm install --no-package-lock
npm run dev
```

Open `http://localhost:3000/`. Set `PORT=3001` to run beside a studio already using port 3000.

The scene editor and local catalog can load without a Gemini key. To use Gemini-generated voice, script assistance, character and video analysis, supply `GEMINI_API_KEY` to the server process via your existing secret-management workflow. Do not put real credentials in public source or client-side code.

```sh
npm run lint
npm run build
```

## Preserved features

- Sam / Stage / SamSpeak / Assets creative workspace and storyboard timeline.
- Environment levels, sky and lighting controls, procedural scene objects, materials, camera transitions and character rigging.
- 3D asset ingestion (GLB, glTF, OBJ, STL, PLY, FBX, DAE), IFC visual import, video, images, audio and transcripts.
- Single-/dual-speaker Gemini TTS, existing voice names and style presets.
- Save/reopen `.samscene.json` projects and export scene geometry as GLB.
- Local `studio_templates` SQLite catalog, exposed through `/api/templates`.

## Persistence boundaries

Local template catalog data is stored in `.data/samscene_templates.sqlite` and is ignored by Git. It is **not** the hosted CMS database. Browser project slots remain stored locally. Imported model/audio/video source files are not yet fully embedded in the `.samscene.json` export; GLB is a presentation export, not an editable source archive.

The existing `@inneranimalmedia/iamscene` and CMS integrations are separate subsequent work; this repository import does not replace or redesign either system.
