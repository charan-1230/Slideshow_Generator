# Video SlideShop - Slideshow Generator

A web-based application that transforms photos into dynamic video slideshows with customizable transitions, background music, and multiple resolution options.

## Features

- **User Authentication**: Secure registration and login system with password hashing
- **Image Upload**: Drag-and-drop or browse file upload functionality
- **Video Creation**: Convert selected images into video slideshows
- **Audio Integration**: Add background music from a pre-loaded audio library
- **Customizable Options**:
  - Multiple resolution support (144p, 360p, 720p, 1080p)
  - Transition effects (Fade, None)
- **Real-time Preview**: Preview generated videos before download

## Live Demo

The application is deployed on Render: https://course-project-eiffel-group-23-kybq.onrender.com/

## Tech Stack

### **Backend**
- **Framework**: Python Flask 3.0.2
- **Database**: CockroachDB (PostgreSQL-compatible)
- **Authentication**: Flask-JWT-Extended, Werkzeug Security
- **Video Processing**: MoviePy 1.0.3
- **Image Processing**: Pillow (PIL) 10.2.0
- **Database Driver**: psycopg2-binary 2.9.9
- **Deployment**: Render

### **Frontend**
- **Languages**: HTML5, CSS3, Vanilla JavaScript
- **AJAX Communication**: XMLHttpRequest (XHR)
- **File Handling**: FormData API for multipart uploads
- **DOM Manipulation**: Native JavaScript (no frameworks)
- **Event Handling**: JavaScript Event Listeners
- **Drag & Drop**: HTML5 Drag and Drop API
- **Local Storage**: Browser localStorage for JWT token management
- **UI Styling**: Custom CSS with responsive design

### **Communication Layer**
- **Protocol**: HTTP/HTTPS RESTful APIs
- **Data Format**: JSON for request/response payloads
- **File Transfer**: Base64 encoding for media storage/retrieval
- **Authentication**: Bearer token (JWT) in Authorization headers
- **Upload Method**: FormData for multipart file uploads
- **Async Operations**: XMLHttpRequest for non-blocking requests

### **Data Storage**
- **Media Storage**: Base64 encoded binary data in database
- **Session Management**: JWT tokens in browser localStorage
- **File Processing**: Server-side image/video manipulation

### **Security**
- **Password Security**: Werkzeug password hashing
- **Token-based Auth**: JWT with expiration
- **Input Validation**: Client and server-side validation
- **SQL Injection Protection**: Parameterized database queries
- **SSL/TLS**: Encrypted database connections

## Project Structure

```
Slideshow_Generator/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── root_base64.txt       # SSL certificate (base64 encoded)
├── README.md             # Project documentation
├── static/               # Static files
│   ├── images/           # Images and logos
│   ├── script/           # JavaScript files
│   │   └── script.js     # Main frontend logic
│   └── styles/           # CSS stylesheets
│       ├── style1.css    # Landing page styles
│       ├── style2.css    # Dashboard styles
│       ├── style3.css    # Video page styles
│       └── styleregister.css # Auth pages styles
└── templates/            # HTML templates
    ├── index.html        # Landing page
    ├── login.html        # Login page
    ├── registration.html # Registration page
    ├── function.html     # Main dashboard
    ├── video.html        # Video creation page
    └── admin.html        # Admin panel
```

## Database Schema

### Users Table
```sql
CREATE TABLE Users (
    Username VARCHAR(255) PRIMARY KEY,
    Email VARCHAR(255) NOT NULL,
    Name VARCHAR(255) NOT NULL,
    Password VARCHAR(255) NOT NULL
);
```

### Images Table
```sql
CREATE TABLE Images (
    Image_Id SERIAL PRIMARY KEY,
    Username VARCHAR(255) NOT NULL,
    Image_name VARCHAR(255) NOT NULL,
    Filetype VARCHAR(100) NOT NULL,
    Img BYTEA NOT NULL
);
```

### Audio Table
```sql
CREATE TABLE Audio (
    Audio_id SERIAL PRIMARY KEY,
    AudioData BYTEA NOT NULL
);
```

## Usage

1. **Register/Login**: Create an account or login with existing credentials
2. **Upload Images**: Use drag-and-drop or file browser to upload images
3. **Create Video**: Navigate to video creation page
4. **Select Content**: Choose images and audio tracks
5. **Customize**: Set resolution and transition effects
6. **Generate**: Create and preview your video slideshow
7. **Download**: Save the generated video to your device

## Dependencies

Key dependencies include:
- Flask 3.0.2
- psycopg2-binary 2.9.9
- moviepy 1.0.3
- Pillow 10.2.0
- Flask-JWT-Extended 4.6.0

See requirements.txt for complete list.

## Known Issues & Limitations

- **Video Processing Performance**: Large video files may experience extended processing times due to server-side video encoding. Complex slideshows with high-resolution images and long durations can take 2-5 minutes to generate.

- **Database Storage Constraints**: CockroachDB has specific limitations that may affect large file operations:

- **Note**: 
  - Use lower resolutions (360p or below) for longer slideshows

- **Audio Limitations**: Background music files must be pre-loaded into the database by administrators - users cannot upload custom audio tracks

---

*Built with ❤️ using **Flask** web framework | Deployed on **Render** cloud platform | Powered by **CockroachDB** distributed SQL database*