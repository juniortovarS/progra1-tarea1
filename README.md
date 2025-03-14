# progra1-tarea1
tarea de programacion I



////codigo del ejercicio///

class SolicitudCredito:
    def __init__(self, nombre, dni, fecha_contratacion, salario, frecuencia_pago, monto_solicitado):
        self.nombre = nombre
        self.dni = dni
        self.fecha_contratacion = fecha_contratacion
        self.salario = salario
        self.frecuencia_pago = frecuencia_pago
        self.monto_solicitado = monto_solicitado
    
    def validar_credito(self):
        if self.monto_solicitado > (0.3 * self.salario):
            return "Rechazado: No puede solicitar más del 30% de su salario."
        
        meses_contratacion = self.calcular_meses_contratacion()
        if meses_contratacion < 3:
            return "Rechazado: Debe tener al menos 3 meses de contratación."
        
        if self.salario > 2000 and self.frecuencia_pago in ["Quincenal", "Mensual"]:
            return "Aprobado: Cumple con los requisitos de salario y frecuencia de pago."
        
        if self.salario <= 2000 and self.frecuencia_pago == "Semanal":
            return "Aprobado: Cumple con los requisitos de salario y frecuencia de pago."
        
        return "Rechazado: No cumple con los requisitos establecidos."
    
    def calcular_meses_contratacion(self):
        from datetime import datetime
        fecha_actual = datetime.now()
        fecha_inicio = datetime.strptime(self.fecha_contratacion, "%Y-%m-%d")
        diferencia_meses = (fecha_actual.year - fecha_inicio.year) * 12 + (fecha_actual.month - fecha_inicio.month)
        return diferencia_meses

# Ejemplo de uso
solicitud = SolicitudCredito("Juan Pérez", "12345678", "2023-01-15", 2500, "Quincenal", 600)
resultado = solicitud.validar_credito()
print(resultado)
