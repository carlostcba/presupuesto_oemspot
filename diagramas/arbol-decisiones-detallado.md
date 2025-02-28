# Árbol de Decisiones Detallado para Elaboración de Presupuesto

Este diagrama muestra el flujo de decisiones que debe seguirse para determinar los componentes necesarios en un sistema de estacionamiento ParkingYa, basándose en las características del establecimiento y sus necesidades específicas.

```mermaid
flowchart TD
    start[Inicio de evaluación] --> tipoEstablecimiento{¿Tipo de establecimiento?}
    
    tipoEstablecimiento -->|Shopping/Centro comercial| rotacionAlta[Alta rotación: >500 veh/día]
    tipoEstablecimiento -->|Universidad/Club| rotacionMedia[Rotación media: 300-500 veh/día]
    tipoEstablecimiento -->|Edificio corporativo| rotacionBaja[Baja rotación: <300 veh/día]
    
    rotacionAlta & rotacionMedia & rotacionBaja --> cantidadAccesos{¿Cantidad de accesos vehiculares?}
    
    cantidadAccesos -->|1-2 accesos| accesoBasico[Configuración básica]
    cantidadAccesos -->|3-5 accesos| accesoMedio[Configuración media]
    cantidadAccesos -->|6+ accesos| accesoAvanzado[Configuración avanzada]
    
    %% Determinación del Server Parking
    accesoBasico --> serverBasico[1 Server Parking - i3 10100, 8GB RAM, 2 SSD 240GB]
    accesoMedio --> serverMedio[1-2 Servers Parking]
    accesoAvanzado --> serverAvanzado[2-3 Servers Parking]
    
    %% Determinación de puestos de cobro
    accesoBasico --> cobroBasico[1 Puesto de cobro]
    accesoMedio --> cobroMedio[1-2 Puestos de cobro]
    accesoAvanzado --> cobroAvanzado[2+ Puestos de cobro]
    
    %% Determinación de barreras vehiculares
    accesoBasico --> barrerasBasico[2 Barreras JG-20000]
    accesoMedio --> barrerasMedio[4-6 Barreras JG-20000]
    accesoAvanzado --> barrerasAvanzado[6+ Barreras JG-20000]
    
    %% Determinación de postes de entrada/salida
    accesoBasico --> postesBasico[1 Poste entrada + 1 Poste salida]
    accesoMedio --> postesMedio[2-3 Postes entrada + 2-3 Postes salida]
    accesoAvanzado --> postesAvanzado[3+ Postes entrada + 3+ Postes salida]
    
    %% Determinación de características específicas
    serverBasico & serverMedio & serverAvanzado --> caracteristicasEspecificas{¿Requerimientos especiales?}
    cobroBasico & cobroMedio & cobroAvanzado --> caracteristicasEspecificas
    barrerasBasico & barrerasMedio & barrerasAvanzado --> caracteristicasEspecificas
    postesBasico & postesMedio & postesAvanzado --> caracteristicasEspecificas
    
    caracteristicasEspecificas -->|Control de altura| incluyeSensor[Incluir sensor de altura]
    caracteristicasEspecificas -->|Control manual| incluyePulsadores[Incluir pulsadores de accionamiento]
    caracteristicasEspecificas -->|Respaldo energético| incluyeUPS[Incluir UPS On Line 2KWA]
    caracteristicasEspecificas -->|Postes avanzados| incluyePostesDobleAltura[Incluir postes doble altura]
    caracteristicasEspecificas -->|Todo incluido| incluyeTodo[Incluir todos los componentes adicionales]
    
    %% Configuración de software
    incluyeSensor & incluyePulsadores & incluyeUPS & incluyePostesDobleAltura & incluyeTodo --> configuracionSoftware{¿Nivel de software?}
    
    configuracionSoftware -->|Básico| softwareBasico[Software Winpark básico]
    configuracionSoftware -->|Intermedio| softwareIntermedio[Software Winpark + Supervisor]
    configuracionSoftware -->|Completo| softwareCompleto[Software Winpark + Supervisor + Gestión]
    
    %% Componentes adicionales
    softwareBasico & softwareIntermedio & softwareCompleto --> convertidores[Convertidores 232/485]
    convertidores --> cantidadConvertidores{¿Cantidad de convertidores?}
    
    cantidadConvertidores -->|Mínimo| convertidoresMinimo[1 Conversor central]
    cantidadConvertidores -->|Estándar| convertidoresEstandar[1 Conversor por par entrada/salida]
    cantidadConvertidores -->|Óptimo| convertidoresOptimo[1 Conversor por entrada/salida]
    
    %% Determinación final del equipamiento
    convertidoresMinimo & convertidoresEstandar & convertidoresOptimo --> configuracionFinal[Configuración final del equipamiento]
    
    %% Esquema comercial
    configuracionFinal --> esquemaComercial{¿Esquema comercial?}
    
    esquemaComercial -->|Opción 1| opcionCompra[Compra equipamiento + Servicio Cloud]
    esquemaComercial -->|Opción 2| opcionServicio[Servicio parking con equipamiento en comodato]
    
    opcionCompra --> porcentajeCompra[5% por transacción]
    opcionCompra --> minimoCompra[Monto mínimo mensual menor]
    
    opcionServicio --> porcentajeServicio[15% por transacción]
    opcionServicio --> minimoServicio[Monto mínimo mensual mayor]
    
    %% Consideraciones adicionales
    porcentajeCompra & minimoCompra & porcentajeServicio & minimoServicio --> consideracionesAdicionales{¿Incluir adicionales?}
    
    consideracionesAdicionales -->|Obra civil| incluirObra[Cotizar obra civil por separado]
    consideracionesAdicionales -->|Lazos inductivos| incluirLazos[Incluir lazos inductivos: ~U$D 240 c/u]
    consideracionesAdicionales -->|Ninguno| excluirAdicionales[Excluir obras y adicionales]
    
    incluirObra & incluirLazos & excluirAdicionales --> calculoFinal[Cálculo final del presupuesto]
    
    calculoFinal --> presupuestoFinal[Generación de propuesta comercial completa]
```

## Cómo utilizar este diagrama

1. **Identificar el tipo de establecimiento** para determinar el volumen de rotación esperado
2. **Evaluar la cantidad de accesos** para seleccionar el nivel de configuración adecuado
3. **Determinar los componentes base** según la configuración (servidores, puestos de cobro, barreras, postes)
4. **Añadir requerimientos especiales** según las necesidades específicas
5. **Definir el nivel de software** requerido
6. **Dimensionar los componentes adicionales**
7. **Seleccionar el esquema comercial** más adecuado
8. **Evaluar consideraciones adicionales** como obra civil y componentes especiales
9. **Realizar el cálculo final** y generar la propuesta comercial
