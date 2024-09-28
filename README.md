Here’s a *short overview* of building the eCommerce website using *Django*:

1. Project Setup*

1. *Install Django & Pillow:*
   bash
   pip install django pillow
   
2. *Start a Django Project & App:*
   bash
   django-admin startproject ecommerce_project
   cd ecommerce_project
   python manage.py startapp shop


2. Database Models*

Create models for *Product, **Order, and **OrderItem* in shop/models.py.

python
from django.db import models
from django.contrib.auth.models import User

class Product(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()
    price = models.DecimalField(max_digits=10, decimal_places=2)
    image = models.ImageField(upload_to='products/')
    stock = models.PositiveIntegerField()

class Order(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    total_price = models.DecimalField(max_digits=10, decimal_places=2)
    shipping_address = models.TextField()

class OrderItem(models.Model):
    order = models.ForeignKey(Order, on_delete=models.CASCADE)
    product = models.ForeignKey(Product, on_delete=models.CASCADE)
    quantity = models.PositiveIntegerField(default=1)


Run migrations:
bash
python manage.py makemigrations shop
python manage.py migrate

3. Product Management*

- *List Products:*
  Create a view to list all products and a detail page for each product.
  
  python
  from django.shortcuts import render
  from .models import Product

  def product_list(request):
      products = Product.objects.all()
      return render(request, 'product_list.html', {'products': products})
  
  def product_detail(request, pk):
      product = Product.objects.get(id=pk)
      return render(request, 'product_detail.html', {'product': product})
  
4. Shopping Cart*

Store the cart in sessions and allow users to *add to cart, **view, and **update* it.

python
def add_to_cart(request, product_id):
    cart = request.session.get('cart', {})
    cart[product_id] = cart.get(product_id, 0) + 1
    request.session['cart'] = cart
    return redirect('view_cart')

def view_cart(request):
    cart = request.session.get('cart', {})
    return render(request, 'cart.html', {'cart': cart})

5. User Authentication*

Use Django's built-in authentication system for *login, **logout, and **register*.

bash
python manage.py createsuperuser  # Create admin for testing

6. Checkout Process*

Create a form for users to enter *shipping details* and show an *order summary*. Save orders and reduce stock when users place an order.

7. Order Management*

Allow users to view their *past orders* in a "My Orders" page.

8. Submit Project*

1. **Create requirements.txt:**
   bash
   pip freeze > requirements.txt
   

2. *README.md:* Include setup instructions and basic usage.

3. *Push to GitHub* with clear commit messages.
