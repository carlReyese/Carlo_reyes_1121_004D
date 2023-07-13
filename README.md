# Carlo_reyes_1121_004D
ET EXAMEN 

precios = {"Platinum": 120000,"Gold": 80000,"Silver": 50000}
entradas_disponibles = [i for i in range(1, 101)]  
entradas_vendidas = []  
asistentes = []
ganancias_totales = 0
tipo_entrada=0

def comprar_entradas():
    cantidad = int(input("Ingrese la cantidad de entradas a comprar (1-3): "))
    if cantidad < 1 or cantidad > 3:
        print("Cantidad inválida. Intente nuevamente.")
        return
    for _ in range(cantidad):
        print("Ubicaciones disponibles:", entradas_disponibles)
        seleccion = int(input("Seleccione una ubicación: ")) 
        if seleccion in entradas_vendidas:
            print("Ubicación no disponible. Intente nuevamente.")
            continue
        entradas_vendidas.append(seleccion)
        entradas_disponibles.remove(seleccion)
        run = input("Ingrese el RUN de la persona (sin guiones ni puntos): ")
        asistentes.append((run, seleccion)) 
    print("Operación realizada correctamente.")

def mostrar_ubicaciones_disponibles():
    print("Ubicaciones disponibles:", entradas_disponibles)
    print("Ubicaciones vendidas:", entradas_vendidas)

def ver_listado_asistentes():
    if not asistentes:
        print("No hay asistentes registrados.")
        return    
    asistentes_ordenados = sorted(asistentes, key=lambda x: x[0])
    print("Listado de asistentes:")
    for run, ubicacion in asistentes_ordenados:
        print(run, "- Ubicación:", ubicacion)

def mostrar_ganancias_totales():
    print("Tipo Entrada Cantidad Total")
    for tipo, precio in precios.items():
        cantidad = entradas_vendidas.count(tipo)
        total = cantidad * precio
        print(f"{tipo} {precio} {cantidad} {total}")
    print("TOTAL", len(entradas_vendidas), ganancias_totales)

def main():
    while True:
        print("--- MENÚ ---")
        print("1. Comprar entradas")
        print("2. Mostrar ubicaciones disponibles")
        print("3. Ver listado de asistentes")
        print("4. Mostrar ganancias totales")
        print("5. Salir")        
        opcion = input("Seleccione una opción del menú: ")
        
        if opcion == "1":
            comprar_entradas()
        elif opcion == "2":
            mostrar_ubicaciones_disponibles()
        elif opcion == "3":
            ver_listado_asistentes()
        elif opcion == "4":
            mostrar_ganancias_totales()
        elif opcion == "5":
            print("Saliendo del sistema...")
            print("¡Gracias por utilizar nuestra aplicación!")
            print("Carlo Reyes, 13/07/2023")
            break
        else:
            print("Opción inválida. Intente nuevamente.")

main()
