# Music Recommendation Chatbot

An intelligent music recommendation system powered by AI that provides personalized song suggestions through a conversational chatbot interface. The application features user feedback collection, recommendation history tracking, and a RESTful API built with Flask.

## Overview

This chatbot-driven music recommendation system analyzes user preferences and provides tailored music suggestions. The application includes a feedback mechanism to improve recommendations over time and maintains a comprehensive history of user interactions.

## Features

- AI-powered music recommendations based on user input
- Interactive chatbot interface for natural conversation
- User feedback collection system for continuous improvement
- SQLite database for persistent storage of feedback and history
- RESTful API with CORS support for frontend integration
- Recommendation history tracking
- Real-time song suggestions based on mood, genre, or artist preferences

## Technology Stack

- **Backend Framework**: Flask
- **Database**: SQLite
- **Machine Learning**: Custom recommendation model
- **CORS Support**: Flask-CORS for cross-origin requests
- **Language**: Python 3.x

## Installation

### Prerequisites

- Python 3.7 or higher
- pip package manager

### Setup Instructions

1. Clone the repository:
```bash
git clone https://github.com/jeevanu345/Music--Recommendation-using-chatbot.git
cd Music--Recommendation-using-chatbot
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

Required packages:
- Flask
- flask-cors
- sqlite3 (included in Python standard library)
- Additional dependencies listed in requirements.txt

3. Initialize the application:
```bash
python app.py
```

4. The server will start on `http://localhost:5000` by default

## API Endpoints

### 1. Get Music Recommendations

**Endpoint**: `/recommend`

**Method**: `POST`

**Request Body**:
```json
{
  "input": "upbeat pop songs"
}
```

**Response**:
```json
{
  "recommendations": [
    "Song 1",
    "Song 2",
    "Song 3"
  ]
}
```

**Description**: Accepts user input describing music preferences and returns a list of recommended songs.

### 2. Submit Feedback

**Endpoint**: `/feedback`

**Method**: `POST`

**Request Body**:
```json
{
  "song": "Song Title",
  "feedback": "loved it"
}
```

**Response**:
```json
{
  "message": "Feedback saved successfully!"
}
```

**Error Response** (400):
```json
{
  "error": "Song and feedback are required"
}
```

**Description**: Allows users to provide feedback on recommended songs for system improvement.

### 3. View Feedback History

**Endpoint**: `/history`

**Method**: `GET`

**Response**:
```json
{
  "history": [
    {
      "id": 1,
      "song": "Song Title",
      "feedback": "loved it"
    }
  ]
}
```

**Description**: Retrieves all stored user feedback and recommendation history.

## Project Structure
```
Music--Recommendation-using-chatbot/
│
├── app.py                      # Main Flask application
├── recommendation_model.py     # AI recommendation logic
├── requirements.txt            # Python dependencies
├── package.json               # Node.js configuration (if applicable)
├── README.md                  # Project documentation
├── Readme.txt                 # Additional notes
├── .gitattributes            # Git configuration
│
└── database/
    └── db.sqlite             # SQLite database (auto-created)
```

## Database Schema

### user_feedback Table

| Column   | Type    | Description                    |
|----------|---------|--------------------------------|
| id       | INTEGER | Primary key (auto-increment)   |
| song     | TEXT    | Song title                     |
| feedback | TEXT    | User feedback text             |

## Usage Examples

### Making a Recommendation Request
```python
import requests

url = "http://localhost:5000/recommend"
data = {"input": "relaxing jazz music"}

response = requests.post(url, json=data)
print(response.json())
```

### Submitting Feedback
```python
import requests

url = "http://localhost:5000/feedback"
data = {
    "song": "Blue in Green",
    "feedback": "Perfect for studying"
}

response = requests.post(url, json=data)
print(response.json())
```

### Retrieving History
```python
import requests

url = "http://localhost:5000/history"
response = requests.get(url)
print(response.json())
```

## Recommendation Model

The recommendation system analyzes user input using natural language processing and machine learning techniques to suggest relevant songs. The model considers:

- User-provided mood or genre keywords
- Artist preferences
- Previous feedback patterns
- Musical characteristics and attributes

Details of the recommendation algorithm can be found in `recommendation_model.py`.

## Configuration

The application uses the following default settings:

- **Debug Mode**: Enabled (should be disabled in production)
- **Host**: localhost
- **Port**: 5000
- **Database Path**: `database/db.sqlite`

To modify these settings, edit the configuration in `app.py`.

## Development

### Running in Development Mode
```bash
python app.py
```

The application will run with debug mode enabled, providing detailed error messages and automatic reloading on code changes.

### Running in Production

For production deployment:

1. Disable debug mode in `app.py`
2. Use a production WSGI server like Gunicorn:
```bash
gunicorn -w 4 app:app
```

## Frontend Integration

The API is CORS-enabled and can be integrated with any frontend framework:

- React
- Vue.js
- Angular
- Plain HTML/JavaScript

Example frontend fetch request:
```javascript
fetch('http://localhost:5000/recommend', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ input: 'energetic workout music' })
})
.then(response => response.json())
.then(data => console.log(data.recommendations));
```

## Future Enhancements

Planned improvements for upcoming versions:

- Integration with Spotify or Apple Music APIs
- Advanced sentiment analysis for feedback processing
- User authentication and personalized profiles
- Collaborative filtering for improved recommendations
- Playlist generation and management
- Audio preview functionality
- Social features for sharing recommendations
- Mobile application development

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

## Known Issues

- Database is created in debug mode; ensure proper directory permissions
- Feedback validation is basic; consider implementing more robust validation
- No user authentication currently implemented

## License

This project is open source and available under the MIT License.

## Contact

For questions or suggestions, please open an issue on the GitHub repository.

## Acknowledgments

- Flask framework for providing a lightweight web server solution
- SQLite for reliable embedded database functionality
- The open-source community for tools and inspiration

---

**Note**: This application is designed for educational and demonstration purposes. For production use, implement proper security measures including authentication, input validation, and error handling.
