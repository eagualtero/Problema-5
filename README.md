"""
Problema 5. Control de Horas Trabajadas por Recurso
"""

# Umbral de horas semanales estandar 
UMBRAL_HORAS = 40

# ---------------------------------------------------------
# Matriz de datos: 4 recursos con horas trabajadas Lun-Vie
# Estructura: [Nombre, Lunes, Martes, Miercoles, Jueves, Viernes]
# ---------------------------------------------------------
matriz_horas = [
    ["Ana Torres",     9, 8, 9, 8, 8],
    ["Luis Fernandez", 8, 8, 8, 8, 8],
    ["Maria Gomez",    7, 7, 8, 7, 7],
    ["Carlos Ruiz",    9, 9, 9, 9, 9],
]


def calcular_horas_totales(recurso):

    horas_dias = recurso[1:]
    return sum(horas_dias)


def clasificar_jornada(total_horas, umbral=UMBRAL_HORAS):
    if total_horas > umbral:
        return "Sobretiempo"
    else:
        return "Horario Estandar"


def procesar_equipo(matriz):
    resultados = []
    for recurso in matriz:
        nombre = recurso[0]
        total_horas = calcular_horas_totales(recurso)
        clasificacion = clasificar_jornada(total_horas)
        resultados.append((nombre, total_horas, clasificacion))
    return resultados


def mostrar_reporte(resultados):
    print("=" * 55)
    print(f"{'REPORTE SEMANAL DE HORAS TRABAJADAS':^55}")
    print("=" * 55)
    print(f"{'Recurso':<20}{'Total Horas':<15}{'Clasificacion':<20}")
    print("-" * 55)

    for nombre, total_horas, clasificacion in resultados:
        print(f"{nombre:<20}{total_horas:<15}{clasificacion:<20}")

    print("=" * 55)


def main():
    """Funcion principal que orquesta la ejecucion del programa."""
    resultados = procesar_equipo(matriz_horas)
    mostrar_reporte(resultados)


if __name__ == "__main__":
    main()

input("preciona ENTER para salir")
