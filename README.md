# Plann.er
Plann.er is a travel organizer API in Java, created during the Rocketseat NLW event. This API allow users to manage trips, activities, participants and links related to trips.

# Technologies
- Java
- Maven
- Spring Boot

# Endpoints

## Trips

### Create Trip

**Endpoint**: `POST /trips`

**Description:** Create a new trip and register the participants.

**Request Body:**
```json
{
  "destination": "string",
  "starts_at": "string (ISO_DATE_TIME)",
  "ends_at": "string (ISO_DATE_TIME)",
  "emails_to_invite": [
    "string"
  ],
  "owner_name": "String",
  "owner_email": "String"
}
```

**Response:**
```json
{
  "id": "UUID"
}
```

### Get trip details

**Endpoint**: `GET /trips/{id}`

**Description:** Return the details of a specific trip.

**Response:**
```json
{
  "id": "UUID",
  "destination": "string",
  "starts_at": "string (ISO_DATE_TIME)",
  "ends_at": "string (ISO_DATE_TIME)",
  "isConfirmed": "boolean",
  "activities": [],
  "participants": [],
  "links": []
}
```

### Update trip

**Endpoint**: `PUT /trips/{id}`

**Description:** Update the details of an existing trip.

**Request Body:**
```json
{
  "destination": "string",
  "starts_at": "string (ISO_DATE_TIME)",
  "ends_at": "string (ISO_DATE_TIME)"
}
```

**Response:**
```json
{
  "id": "UUID",
  "destination": "string",
  "starts_at": "string (ISO_DATE_TIME)",
  "ends_at": "string (ISO_DATE_TIME)",
  "isConfirmed": "boolean"
}
```

### Confirm trip

**Endpoint**: `GET /trips/{id}/confirm`

**Description:** Confirm a trip and send confirmation e-mail to participants.

**Response:**
```json
{
  "id": "UUID",
  "isConfirmed": "boolean"
}
```

## Activities

### Create activity

**Endpoint**: `POST /trips/{id}/activities`

**Description:** Create a new activity for a specific trip.

**Request:**
```json
{
  "title": "string",
  "occurs_at": "string (ISO_DATE_TIME)"
}
```

**Response:**
```json
{
  "id": "UUID",
  "title": "string",
  "occurs_at": "string (ISO_DATE_TIME)"
}
```

### Get all the activities

**Endpoint**: `GET /trips/{id}/activities`

**Description:** Return all activities for a specific trip.

**Response:**
```json
[
  {
    "id": "UUID",
    "title": "string",
    "occurs_at": "string (ISO_DATE_TIME)"
  }
]
```

## Participants

### Invite participant

**Endpoint**: `POST /trips/{id}/invite`

**Description:** Invite a participant for a specific trip.

**Request:**
```json
{
  "email": "string"
}
```

**Response:**
```json
{
  "id": "UUID",
}
```

### Get all the participants

**Endpoint**: `GET /trips/{id}/participants`

**Description:** Return all the participants for a specific trip

**Response:**
```json
[
  {
    "id": "UUID",
    "name": "string",
    "email": "string"
  }
]
```

## Links

### Register link

**Endpoint**: `POST /trips/{id}/links`

**Description:** Register a new link for a specific trip.

**Request:**
```json
{
  "url": "string",
  "title": "string"
}
```

**Response:**
```json
{
  "id": "UUID",
  "url": "string",
  "title": "string"
}
```

### Return all links

**Endpoint**: `GET /trips/{id}/links`

**Description:** Return all links from a specific trip.

**Response:**
```json
[
  {
    "id": "UUID",
    "url": "string",
    "title": "string"
  }
]
```
