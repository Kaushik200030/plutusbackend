The following documentation outlines the API endpoints based on requirements of project.

## Admin UI
[Deployed Version Backend](http://kaushikpattnaik200030.pythonanywhere.com/admin)
- `username`: "admin"
- `password`: "admin123"

## Frontend
[Deployed Version Frontend](https://eloquent-lebkuchen-275dc5.netlify.app/posts)
- `repository`: [Link](https://github.com/Kaushik200030/frontend)
- Use same credentials as above to login
- Scroll down on home page to register

---

### **1. Sign Up (Registration) API**

**Endpoint:** `/api/signup`

**Method:** `POST`

**Functionality:** Allows a new user to create an account.

**Headers:**

- `Content-Type: application/json`

**Body Data Parameters:**

- `username` - Desired username for the new account.
- `email` - Email address for the new account.
- `password` - Password for the new account.

**Authorization Required:** No

### Sign Up (Registration)
```bash
curl --location --request POST 'http://kaushikpattnaik200030.pythonanywhere.com/api/signup' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "username",
    "email": "email@abc.com",
    "password": "password"
}'
```

---

### **2. Login API**

**Endpoint:** `/api/login`

**Method:** `POST`

**Functionality:** Authenticates a user and provides a token for accessing protected endpoints.

**Headers:**

- `Content-Type: application/json`

**Body Data Parameters:**

- `username` - The user's username.
- `password` - The user's password.

**Authorization Required:** No

### Login
```bash
curl --location --request POST 'http://kaushikpattnaik200030.pythonanywhere.com/api/login' \
--header 'Content-Type: application/json' \
--data-raw '{
   "username": "username",
   "password": "password"
}'
```

---

### **3. Fetch Posts API (General)**

**Endpoint:** `/api/posts/`

**Method:** `GET`

**Functionality:** Retrieves a list of all posts.

**Headers:** None required for this action.

**Body Data Parameters:** None - The third curl example does not specify any data, suggesting that this endpoint may be a simple GET request without a body.

**Authorization Required:** No

### Fetch Posts (General)
```bash
curl --location --request GET 'http://kaushikpattnaik200030.pythonanywhere.com/api/posts/'
```

---

### **4. Fetch Posts by User API**

**Endpoint:** `/api/posts/?user={user_id}`

**Method:** `GET`

**Functionality:** Retrieves a list of posts by a specific user.

**Headers:** No headers required for this action.

**Body Data Parameters:** None - The endpoint appears to use a query parameter `user` to filter posts by the user ID.

**Authorization Required:** No

### Fetch Posts by User
```bash
curl --location --request GET 'http://kaushikpattnaik200030.pythonanywhere.com/api/posts/?user=<user_id>'
```

---

### **5. Create Comment API**

**Endpoint:** `/api/comments/`

**Method:** `POST`

**Functionality:** Allows a user to add a comment to a post.

**Headers:**

- `Content-Type: application/json`
- `Authorization: Token your_token`

**Body Data Parameters:**

- `post` - The ID of the post to comment on.
- `body` - The content of the comment.

**Authorization Required:** Yes - A valid token must be provided in the `Authorization` header.

### Create Comment
```bash
curl --location --request POST 'http://kaushikpattnaik200030.pythonanywhere.com/api/comments/' \
--header 'Content-Type: application/json' \
--header 'Authorization: Token <your_token>' \
--data-raw '{
  "post": "<your_post_id>",
  "body": "<your_comment_body>"
}'
```

---

### **6. Like a Post API**

**Endpoint:** `/api/likes/`

**Method:** `POST`

**Functionality:** Allows a user to like a post.

**Headers:**

- `Content-Type: application/json`
- `Authorization: Token your_token`

**Body Data Parameters:**

- `post` - The ID of the post to like.

**Authorization Required:** Yes - A valid token must be provided in the `Authorization` header.

### Like a Post
```bash
curl --location --request POST 'http://kaushikpattnaik200030.pythonanywhere.com/api/likes/' \
--header 'Content-Type: application/json' \
--header 'Authorization: Token <your_token>' \
--data-raw '{
  "post": "<your_post_id>"
}'
```

---

### **7. Create Post API**

**Endpoint:** `/api/posts/`

**Method:** `POST`

**Functionality:** Allows a user to create a new post.

**Headers:**

- `Content-Type: application/json`
- `Authorization: Token your_token`

**Body Data Parameters:**

- `title` - The title of the post.
- `body` - The content of the post.

**Authorization Required:** Yes - A valid token must be provided in the `Authorization` header.

### Create Post
```bash
curl --location --request POST 'http://kaushikpattnaik200030.pythonanywhere.com/api/posts/' \
--header 'Content-Type: application/json' \
--header 'Authorization: Token <your_token>' \
--data-raw '{
  "title": "<your_post_title>",
  "body": "<your_post_body>"
}'
```

---

**Note:** For Headers requiring the `Authorization` token, replace `your_token` with the actual token received after authentication. For Body Data parameters containing the `your_` prefix, replace with actual content values when making the request.

This documentation provides a basic overview for each API's functionality and usage. For a full integration, additional details such as error handling, response structures, and status codes should be considered and documented appropriately.
