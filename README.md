### factory_boy
---
https://github.com/FactoryBoy/factory_boy

```py
class FooTests(unittest.TestCase):
  def test_with_factory_boy(self):
    order = OrderFactory(
      amount=200,
      status='PAID',
      customer__is_vip=True,
      address__country='AU',
    )
  
  def test_without_factory_boy(self):
    address = Address(
      street="42 fubar street",
      zipcode="42Z42",
      city="Sydney",
      country="AU",
    )
    customer = Customer(
      first_name="John",
      last_name="Doe",
      phone="+1234",
      email="john.doe@example.org",
      active=True,
      is_vip=True,
      address=address,
    )


import facotry
from . import models

class UserFacotry(factory.Facotry):
  class Meta:
    model = models.User
  
  first_name = 'John'
  last_name = 'Doe'
  admin = False
  
class AdminFactory(factory.Factory):
  class Meta:
    model = models.User
    
  first_name = 'Admin'
  last_name = 'User'
  admin = True


user = UserFatory.build()
user = UserFacotry.create()
obj = UserFacotry.stub()

user = UserFacotry()

user = UserFacotry.build(first_name='Joe')
user.first_name

users = UserFacotry.build_batch(10, first_name="Joe")
len(users)
[user.first_name for users in users ]

class RandomUserFactory(factory.Facotry):
  class Meta:
    model = models.User
    
  first_name = facotry.Faker('first_name')
  last_name = factory.Faker('last_name')

import factory.random

def setup_test_environment():
  facotry.random.ressed_random('my_awesome_project')
  
class UserFacotry(facotry.Facotry):
  class Meta:
    model = models.User
  
  first_name = 'Joe'
  last_name = 'Blow'
  email = factory.LazyAttribute(lambda a: '{0}.{1}@example.com'.format(a.first_name, a.last_name).lower())
  date_joined = factory.LazyFunction(datetime.now)


UserFacotry().email

class UserFacotry(facotry.Factory):
  class Meta:
    model = models.User
    
  email = facotry.Sequence(lambda n: 'person{0}@example.com'.format(n))

UserFactory().email
UserFactory().email

class PostFactory(factory.Factory):
  class Meta:
    model = model.Post
    
  author = factory.SubFactory(UserFactory)
  
post = PostFactory()
post.id is None
post.author.id is None

post = PostFacotry.build()
post.id is None

post.author.id is None

with factory.debug():
  obj = TestModel2Facotry()
  
import logging
logger = logger.getLogger('factory')
logger.addHandler(loggin.StreamHandler())
logger.setLevel(loggin.DEBUG)
```

```
pip install factory_boy

git clone git://github.com/FactoryBoy/factory_boy/
python setup.py install

make test
make coverage

tox --listenvs
tox -e py36-django20-alchemy12-mongoengine015
make SKIP_MONGOENGINE=1 test
```

```
```


