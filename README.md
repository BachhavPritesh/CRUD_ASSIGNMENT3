# Notes API

Backend notes API with CRUD, search, filter, sort, and pagination.

## Setup

```bash
npm install
```

## Environment

Create `.env` file:

```
MONGO_URI=mongodb://localhost:27017/notes-db
PORT=5000
```

## Run

```bash
npm start        # production
npm run dev      # development (nodemon)
```

## Endpoints

### CRUD

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/notes | Create note |
| POST | /api/notes/bulk | Create bulk notes |
| GET | /api/notes | Get all notes |
| GET | /api/notes/:id | Get note by ID |
| PUT | /api/notes/:id | Replace note |
| PATCH | /api/notes/:id | Update note |
| DELETE | /api/notes/:id | Delete note |
| DELETE | /api/notes/bulk | Delete bulk notes |

### Search

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/notes/search | Search by title |
| GET | /api/notes/search/content | Search by content |
| GET | /api/notes/search/all | Search title + content |

### Combined

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/notes/filter-sort | Filter + Sort |
| GET | /api/notes/filter-paginate | Filter + Paginate |
| GET | /api/notes/sort-paginate | Sort + Paginate |
| GET | /api/notes/search-filter | Search + Filter |
| GET | /api/notes/search-sort-paginate | Search + Sort + Paginate |
| GET | /api/notes/filter-sort-paginate | Filter + Sort + Paginate |
| GET | /api/notes/query | Master endpoint |

## Query Parameters

- `q` - Search keyword
- `category` - Filter by category (work, personal, study)
- `isPinned` - Filter by pinned status (true, false)
- `sortBy` - Sort field (title, createdAt, updatedAt, category)
- `order` - Sort order (asc, desc)
- `page` - Page number
- `limit` - Results per page

## Response Format

```json
{
  "success": true,
  "message": "Notes fetched successfully",
  "count": 10,
  "data": []
}
```

Paginated response includes `pagination` object with `total`, `page`, `limit`, `totalPages`, `hasNextPage`, `hasPrevPage`.