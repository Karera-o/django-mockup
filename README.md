# Django Mockup 🧪

**Effortless Test Data Generation for Django Models with AI**

A powerful, intelligent Django library that automatically generates realistic test data for your models using AI-powered algorithms. Django Mockup eliminates the tedious process of manually creating test data by intelligently analyzing your model structure and generating appropriate values that respect all constraints and relationships.

## What is Django Mockup? 🤔

Django Mockup solves one of the most common challenges in development and testing: creating realistic, coherent test data. Rather than writing endless test fixtures or filling databases with meaningless placeholder values, Django Mockup uses AI-driven generation to produce data that:

- **Looks Real**: Names that sound like actual people, addresses that could exist, descriptive product details
- **Maintains Integrity**: Respects all model constraints, field types, and relationships
- **Saves Time**: Generates hundreds of realistic instances in seconds
- **Enhances Testing**: Creates edge cases and diverse data scenarios automatically

The library leverages AI to understand context and generate appropriate values - email addresses look like emails, product descriptions are coherent and relevant, and related models maintain logical connections.

## Features ✨

- **🧠 AI-Powered Generation** - Creates intelligent, contextually appropriate data using advanced algorithms
- **🔄 Direct Model Integration** - Works with Django model classes without any conversion or configuration
- **📊 Smart Field Analysis** - Automatically determines appropriate values based on field names and types
- **🔗 Relationship Handling** - Intelligently manages foreign keys and many-to-many relationships
- **🔧 Customizable Values** - Override specific fields with your own values when needed
- **📱 Command Line Interface** - Generate data directly from the Django management commands
- **🔄 Reproducible Results** - Support for random seeds to generate consistent test data
- **🌐 Multi-Lingual Support** - Generate localized data that fits different regional patterns

## Installation 📦

```bash
pip install django-mockup
```

## Quick Start 🚀

```python
from django_mockup import generate_for_model
from myapp.models import Product

# Generate 5 product instances with AI-powered realistic data
products = generate_for_model(Product, count=5)

# Generate and save to database
saved_products = generate_for_model(Product, count=3, save=True)

# Customize specific fields
custom_products = generate_for_model(
    Product,
    count=2,
    name="Premium Product",
    price=99.99
)
```

## AI Data Generation 🤖

Django Mockup's AI capabilities analyze your model structure to generate contextually appropriate data:

- **Smart Field Recognition**: Identifies field purposes based on names and types
- **Contextual Generation**: Creates related data that makes sense together
- **Pattern Learning**: Generates data following expected patterns for each field type
- **Constraint Awareness**: Respects field constraints like max_length, choices, and validators

For example, for a `Product` model with `name`, `description`, and `category` fields, Django Mockup will generate product names that sound like products, descriptions that match those products, and ensure they fit within the assigned category.

## Usage Examples 📚

### Working with Model Instances

```python
from django_mockup import generate_for_model
from myapp.models import Customer

# Create 10 customers with AI-generated realistic data
customers = generate_for_model(Customer, count=10)

# Print generated data
for customer in customers:
    print(f"{customer.first_name} {customer.last_name} - {customer.email}")
    # Outputs realistic names and matching email addresses
```

### Handling Relationships

```python
from django_mockup import generate_for_model
from myapp.models import Category, Product

# Generate categories first
categories = generate_for_model(Category, count=3, save=True)

# Create products in a specific category
products = generate_for_model(
    Product, 
    count=5,
    category=categories[0]  # Use a specific category
)
```

### Command Line Usage

Generate test data directly from the command line:

```bash
# Generate 10 products
python manage.py generate_instances --model=myapp.Product --count=10

# Generate and save to database
python manage.py generate_instances --model=myapp.Product --count=5 --save

# Generate for all models in an app
python manage.py generate_instances --app=myapp --count=3
```

## Supported Field Types 🧩

Django Mockup automatically handles all standard Django field types with intelligent data generation:

- **Text Fields**: CharField, TextField, EmailField, URLField, SlugField, etc.
- **Numeric Fields**: IntegerField, FloatField, DecimalField, PositiveIntegerField, etc.
- **Boolean Fields**: BooleanField, NullBooleanField
- **Date/Time Fields**: DateField, DateTimeField, TimeField
- **Relationship Fields**: ForeignKey, OneToOneField, ManyToManyField
- **Special Fields**: UUIDField, JSONField, FileField, ImageField, etc.

## Configuration ⚙️

No configuration is required to get started, but you can customize behavior:

```python
from django_mockup import DjangoInstanceGenerator

# Create a generator with a fixed seed for reproducible results
generator = DjangoInstanceGenerator(seed=12345)

# Generate instances with AI-powered data
products = generator.generate_for_model(Product, count=5)
```

## Advanced Usage 🧠

### Generate for an Entire App

```python
from django_mockup import generate_for_all_models

# Generate instances for all models in the 'myapp' app
all_instances = generate_for_all_models(
    'myapp',
    count=3,
    exclude=['LogEntry', 'Session']  # Skip certain models
)

for model, instances in all_instances.items():
    print(f"Generated {len(instances)} instances of {model.__name__}")
```

### Use Without Directly Importing Models

```python
from django_mockup import generate_for_model_path

# Generate model instances by path string
users = generate_for_model_path('myapp.models.User', count=5)
```

### Control AI Generation Flavor

```python
from django_mockup import DjangoInstanceGenerator

# Create a generator with specific AI generation settings
generator = DjangoInstanceGenerator(
    ai_flavor='creative',  # Options: 'realistic', 'creative', 'minimal'
    locale='en_GB'         # Generate UK-specific data
)

# Generate instances with specified AI flavor
products = generator.generate_for_model(Product, count=5)
```

## Contributing 🤝

Contributions are welcome! Feel free to open issues or submit pull requests.

1. Fork the repository
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

## License 📄

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
