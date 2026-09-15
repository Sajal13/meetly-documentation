# API Standards

## Versioning
All APIs use `/api/v1`.

## Success response
```json
{
  "success": true,
  "data": {}
}
```

## Paginated response
```json
{
  "success": true,
  "data": [],
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 100,
    "totalPages": 5
  }
}
```

## Error response
```json
{
  "success": false,
  "error": {
    "code": "EVENT_NOT_FOUND",
    "message": "Event not found"
  }
}
```

## Endpoint contract
Every endpoint must document:
- Method
- URL
- Authentication
- Permission
- Path parameters
- Query parameters
- Request body
- Response
- Error responses
- Business rules

## API rules
- Validate all external input.
- Never trust client-calculated money.
- Never trust client identity/role/permission claims.
- Use idempotency where duplicate requests can cause financial or inventory side effects.
- Return stable machine-readable error codes.
- Generate Swagger/OpenAPI documentation.
