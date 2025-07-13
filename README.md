# RETO-8
Para este reto simplemente en la clase order, creo el iter que me devuelva la lista de self.orders y asi ya se puede iterar la clase. 
```python
class Order:
    def __init__(self, number):
        self.number = number

    def add_items(self, menu_item: MenuItem, quantity: int) -> list:
        self.order=[]
        order = namedtuple (f"Orden{self.number}",["orden","cantidad"])
        i_order= order( 
            menu_item,
            quantity         
        )
        self.order.append(i_order)
    
    def show_order(self):
        return [f"{item.name}, {quantity}" for item, quantity in self.order]
 
    def calculate_bill(self) -> str:
        real_bill = 0
        total_quantity = 0
        names = []
        for menu_item, quantity in self.order:
            names.append(menu_item.name)
            real_bill += menu_item.calculate_price(quantity)
            total_quantity += quantity

        discount_options = [real_bill]
        if total_quantity >= 10:
            discount_options.append(real_bill * 0.9)
        if "Hamburger" in names and "Coca_cola" in names:
            discount_options.append(real_bill * 0.7)
        elif "Ice_cream" in names and "Chocolate_cake" in names:
            discount_options.append(real_bill * 0.8)

        discount_bill = min(discount_options)
        return f"Valor sin descuento {round(real_bill, 2)}, Valor con descuento {round(discount_bill, 2)}"

    
    def __iter__(self):
        return iter(self.order)  
 ```
No es mucho pero es q tocaba estudiar para otras cosas v:
