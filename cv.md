# Arsen Khakimov
## Frontend Developer

### Contact information:

- **Phone:** +996 505 222 478
- **E-mail:** xakars02@gmail.com
- **Telegram:** @arsxak
- [LinkedIn](https://www.linkedin.com/in/arsen-hakimov-77b181176/)

### Skills and Proficiency:
- HTML, CSS, 
- Git, GitHub
- Python, Django, SQL
- Docker, K8s
- Jira, TeamCity

### Code example:
```python
@transaction.atomic
@api_view(['POST'])
def register_order(request):
    client_order = request.data
    serializer = OrserSerializer(data=client_order)
    serializer.is_valid(raise_exception=True)

    order = Order.objects.create(
        address=client_order['address'],
        firstname=client_order['firstname'],
        lastname=client_order['lastname'],
        phonenumber=client_order['phonenumber']
    )

    products = Product.objects.available()
    product_prices = {}
    for product in products:
        product_prices[product.id] = product.price
    product_card = [OrderDetail(
        order=order,
        product_id=product['product'],
        amount=product['quantity'],
        position_price=product_prices[product['product']]
        ) for product in client_order['products']]
    OrderDetail.objects.bulk_create(product_card)

    serializer = OrserSerializer(order)
    return Response(serializer.data)
```
