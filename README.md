# Team Bandwidth Planner

A small Express app for recording each team member's allocated and available hours and seeing how loaded the team is. It is meant for team leads sketching out capacity for a week or sprint.

## Features

- Record allocated and available hours per person
- Calculates a utilization percentage for each entry
- Returns team-wide totals for allocated and available hours
- Saves entries to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3025. Add an entry and read the team back:

```bash
curl -X POST http://localhost:3025/api/capacity \
  -H "Content-Type: application/json" \
  -d '{"person":"Sam","allocated":30,"available":40}'

curl http://localhost:3025/api/capacity
```

## How it works

- `server.js` is an Express server with `POST /api/capacity` and `GET /api/capacity`. The GET response includes the 20 most recent entries and team totals.
- Entries are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API.
- `utils.js` contains validation and stats helpers that `server.js` does not use yet.

## Status

Prototype. The API works and saves to a local JSON file; the web page is not wired up, and there is no input validation or authentication.

## License

MIT, see [LICENSE](LICENSE).
