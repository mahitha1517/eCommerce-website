This Django blog application project allows users to create, view, and comment on blogs. The key components of the application include user authentication, profile management, blog posting, and commenting.

Key Features:
User Authentication:

Users can register and log in using the provided forms.
Login is handled by Django's authenticate() function, and users are redirected based on their authentication status.
Profile Management:

Each user has a profile page where they can upload a profile picture and add social media links (LinkedIn, Instagram, Facebook).
Users can view and edit their profile information.
Blog Posting:

Logged-in users can add new blog posts.
Blog posts include title, author, content, and an optional image.
Only the author of a post can edit or delete their blog post.
Commenting System:

Users can comment on blog posts.
Each blog post displays its comments below, along with the commenter's username and timestamp.
Users must be logged in to comment.
Project Structure:
Navigation Bar: Contains links to home, add blog, profile, and logout options (if logged in), or register and login options (if not logged in).
Database Models:
Profile: Stores user info like bio, social media links, and profile image.
BlogPost: Contains blog post details such as title, author, content, and image.
Comment: Stores comments on blog posts.
Templates: The base HTML page (base.html) defines the layout and is extended by other templates like blog.html, register.html, and profile.html.
Views: Handles HTTP requests for tasks like user registration, login, profile display, blog creation, and comment posting.
This project provides a robust foundation for building a more complex blogging platform with features like searching blogs, user notifications, or enhanced commenting features.
