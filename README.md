# Shopping-_Cart_Inheritance.py
Shopping Cart Inheritance - Multiple Products Types (Electronics + Clothing)

# Day 4 File 2 – INHERITANCE (Company Architecture!)
print("🏪 E-COMMERCE v4.1 - INHERITANCE POWER!")

# BASE CLASS (Parent)
class Product:
    """Base product - ALL products inherit this"""
    def __init__(self, name, price):
        self.name = name
        self.price = price
    
    def display(self):
        return f"📱 {self.name} - ₹{self.price:,}"

# INHERITANCE (Child extends Parent)
class ElectronicsProduct(Product):  # ← Inherits Product!
    """Electronics = Product + warranty"""
    def __init__(self, name, price, warranty_years):
        super().__init__(name, price)  # ← Call Parent constructor
        self.warranty = warranty_years
    
    def display(self):  # ← OVERRIDE parent method
        return f"🔌 {self.name} - ₹{self.price:,} (Warranty: {self.warranty}yr)"

class ClothingProduct(Product):  # ← Also inherits Product!
    """Clothing = Product + size"""
    def __init__(self, name, price, size):
        super().__init__(name, price)
        self.size = size
    
    def display(self):
        return f"👕 {self.name} - ₹{self.price:,} (Size: {self.size})"

# ADVANCED CART (Multiple product types!)
class ShoppingCart:
    def __init__(self):
        self.items = []
    
    def add_item(self, product, qty=1):
        self.items.append({"product": product, "qty": qty})
        return f"✅ Added {qty}x {product.name}"
    
    def show_receipt(self):
        if not self.items:
            return "🛒 Cart empty!"
        
        total = 0
        print("
🛒 YOUR RECEIPT:")
        for item in self.items:
            subtotal = item["product"].price * item["qty"]
            total += subtotal
            print(f"  {item['qty']}x {item['product'].display()}: ₹{subtotal:,}")
        print(f"
💰 TOTAL: ₹{total:,}")
        return total

# CREATE MIXED PRODUCTS (Real store!)
iphone = ElectronicsProduct("iPhone 16", 89000, 1)     # Electronics
tshirt = ClothingProduct("Nike T-Shirt", 1500, "M")     # Clothing  
laptop = ElectronicsProduct("MacBook Air", 120000, 2)   # Electronics

# REAL SHOPPING (Mixed categories!)
cart = ShoppingCart()
print(iphone.display())
print(tshirt.display())
print(laptop.display())

print(cart.add_item(iphone))
print(cart.add_item(tshirt, 3))
print(cart.add_item(laptop))

cart.show_receipt()
