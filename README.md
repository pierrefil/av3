import numpy as np

def derivada_diferencas_finitas(f, x, h=1e-5, metodo='central'):
    """
    Aproxima a derivada de uma função f no ponto x usando diferenças finitas.

    Parâmetros:
        f (callable): Função a ser derivada
        x (float): Ponto onde se quer a derivada
        h (float): Incremento (padrão: 1e-5)
        metodo (str): 'progressiva', 'regressiva' ou 'central'

    Retorna:
        float: valor aproximado da derivada
    """
    if metodo == 'progressiva':
        return (f(x + h) - f(x)) / h
    elif metodo == 'regressiva':
        return (f(x) - f(x - h)) / h
    elif metodo == 'central':
        return (f(x + h) - f(x - h)) / (2 * h)
    else:
        raise ValueError("Método deve ser 'progressiva', 'regressiva' ou 'central'")

# Exemplo de uso
if __name__ == "__main__":
    import math

    func = math.sin
    x0 = 1.0

    for metodo in ['progressiva', 'regressiva', 'central']:
        derivada = derivada_diferencas_finitas(func, x0, metodo=metodo)
        print(f"Derivada de sin(x) em x = {x0} usando {metodo}: {derivada:.6f}")
