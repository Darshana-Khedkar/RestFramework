# Django Movie Categorization API

## Overview
This is a Django-based REST API project that categorizes movies into different genres such as Action, Romantic, and others. It utilizes Django REST Framework (DRF) and provides endpoints for managing movie categories.

## Features
- **Movie Categorization**: Supports multiple genres like Action and Romantic.
- **REST API**: Built with Django REST Framework.
- **Admin Panel**: Manage movies via Django's built-in admin interface.
- **Media Handling**: Supports media file uploads.

## Project Structure
```
mysite/
    ├── movies/
    │   ├── views.py
    │   ├── urls.py
    │   ├── models.py
    ├── mysite/
    │   ├── settings.py
    │   ├── urls.py
    ├── manage.py
```

## URL Routing
```python
from django.contrib import admin
from django.urls import include, path
from rest_framework import routers
from movies.views import MovieViewSet, ActionViewSet, RomanticViewSet
from django.conf.urls.static import static
from django.conf import settings

router = routers.SimpleRouter()
router.register('movies', MovieViewSet, basename="movies")
router.register('action', ActionViewSet, basename="action")
router.register('romantic', RomanticViewSet, basename="romantic")

urlpatterns = [
    path('', include(router.urls)),
    path('admin/', admin.site.urls),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

## API Endpoints
| Endpoint           | Method | Description                   |
|-------------------|--------|-------------------------------|
| `/movies/`       | GET    | List all movies              |
| `/movies/`       | POST   | Add a new movie              |
| `/action/`       | GET    | List all action movies       |
| `/romantic/`     | GET    | List all romantic movies     |

## Setup and Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd mysite
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Apply migrations:
   ```bash
   python manage.py migrate
   ```
4. Run the Django server:
   ```bash
   python manage.py runserver
   ```
5. Access the API at `http://127.0.0.1:8000/`.

## Future Enhancements
- Implement user authentication.
- Add more movie categories dynamically.
- Improve search and filtering options.
 

