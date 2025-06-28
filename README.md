# Sistema de Gestión de Menú y Pedidos - Restaurante

Este proyecto corresponde a una práctica de laboratorio, cuyo propósito es simular un sistema básico de gestión de menús y procesamiento de pedidos en un restaurante. Está desarrollado en lenguaje Python y utiliza estructuras fundamentales como listas, tuplas y diccionarios.

---

## Objetivo

Aplicar conocimientos básicos de programación en Python, tales como:

- Diccionarios anidados
- Tuplas
- Listas
- Condicionales (`if`, `else`)
- Bucles (`while`)
- Entrada de datos con `input()`

---

## Código fuente

```python
# main.py

# -----------------------------
# Sistema de Menú de Restaurante
# -----------------------------

# Diccionario con los platos disponibles
menu_restaurante = {
    "pizza margarita": {
        "nombre": "Pizza Margarita",
        "precio": 8.50,
        "ingredientes": ("tomate", "mozzarella", "albahaca")
    },
    "ensalada césar": {
        "nombre": "Ensalada César",
        "precio": 6.75,
        "ingredientes": ("lechuga", "pollo", "queso parmesano", "croutones")
    },
    "pasta carbonara": {
        "nombre": "Pasta Carbonara",
        "precio": 9.25,
        "ingredientes": ("pasta", "tocino", "huevo", "queso")
    },
    "hamburguesa clásica": {
        "nombre": "Hamburguesa Clásica",
        "precio": 7.50,
        "ingredientes": ("pan", "carne", "queso", "lechuga", "tomate")
    },
    "sopa de mariscos": {
        "nombre": "Sopa de Mariscos",
        "precio": 10.00,
        "ingredientes": ("camarones", "calamar", "pescado", "cebolla")
    },
    "arroz con pollo": {
        "nombre": "Arroz con Pollo",
        "precio": 7.80,
        "ingredientes": ("arroz", "pollo", "zanahoria", "guisantes")
    },
    "lasaña de verduras": {
        "nombre": "Lasaña de Verduras",
        "precio": 8.00,
        "ingredientes": ("berenjena", "tomate", "queso ricota", "espinaca")
    }
}

# Función para mostrar el menú del restaurante
def mostrar_menu(menu):
    """Muestra el menú del restaurante."""
    print("\n======= MENÚ DEL RESTAURANTE =======\n")
    for clave, datos in menu.items():
        print(f"{datos['nombre']} - ${datos['precio']:.2f}")
        ingredientes = ", ".join(datos["ingredientes"])
        print(f"  Ingredientes: {ingredientes}\n")

# Mostrar el menú inicial
mostrar_menu(menu_restaurante)

# Inicialización de variables del pedido
pedido_actual = []
total_cuenta = 0.0

# Bucle principal para capturar pedidos
while True:
    entrada = input("Escriba el nombre del plato (o 'fin' para terminar): ").strip().lower()
    if entrada == "fin":
        break
    if entrada in menu_restaurante:
        plato = menu_restaurante[entrada]
        pedido_actual.append(plato["nombre"])
        total_cuenta += plato["precio"]
        print(f"{plato['nombre']} añadido al pedido.\n")
    else:
        print("Ese plato no está en el menú. Intente con otro.\n")

# Mostrar el resumen del pedido realizado
print("\n========= RESUMEN DEL PEDIDO =========\n")
if pedido_actual:
    for p in pedido_actual:
        print(f"- {p}")
    print(f"\nTotal a pagar: ${total_cuenta:.2f}")
else:
    print("No se realizaron pedidos.")
