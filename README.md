# MultiEnv Ticket Management System

A full-stack application using Flask for both frontend and backend services, demonstrating environment-specific ticket management.
Screenshots are saved in the Evidence Folder for reference.

## Project Structure

```
multienv/
├── docker-compose.yml
├── backend/
│   ├── dev/
│   │   ├── app.py
│   │   ├── requirements.txt
│   │   ├── Dockerfile
│   │   └── .env
│   └── prod/
│       ├── app.py
│       ├── requirements.txt
│       ├── Dockerfile
│       └── .env
└── frontend/
    ├── app.py
    ├── requirements.txt
    ├── Dockerfile
    └── .env
```

## Environment Configuration

### Backend Development Environment (.env)
```
PORT=3001
MONGO_URI=MONGO_URI=mongodb+srv://winsen1983_db_user:senthil123@cluster01.ylgdylz.mongodb.net/tickets_dev
```

### Backend Production Environment (.env)
```
PORT=3002
MONGO_URI=mongodb+srv://winsen1983_db_user:senthil123@cluster01.ylgdylz.mongodb.net/tickets_prod
```



### Requirements
```
flask==2.0.1
flask-cors==3.0.10
python-dotenv==0.19.0
pymongo==3.12.0
requests==2.26.0
```



### Using Docker Compose
```bash
docker-compose up
```

## Accessing the Application

- Frontend: http://localhost:3000/
- Development Environment: http://localhost:3001/dev
- Production Environment: http://localhost:3002/prod



## Security Considerations

- Never commit `.env` files to version control
- Use different MongoDB databases for dev and prod
- Implement proper authentication
- Use secure headers


