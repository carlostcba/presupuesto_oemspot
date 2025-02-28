# Selección de Componentes para Sistema de Estacionamiento

Este diagrama muestra el proceso detallado para seleccionar los componentes específicos que deben incluirse en un sistema de estacionamiento ParkingYa, basándose en la configuración de entradas y salidas, así como en requerimientos especiales.

```mermaid
flowchart TD
    start[Evaluación de necesidades] --> evaluacionEntradas{¿Cuántas entradas?}
    start --> evaluacionSalidas{¿Cuántas salidas?}
    
    %% Determinación de postes de entrada
    evaluacionEntradas -->|1 entrada| posteE1[1 Poste de entrada]
    evaluacionEntradas -->|2 entradas| posteE2[2 Postes de entrada]
    evaluacionEntradas -->|3+ entradas| posteE3[3+ Postes de entrada]
    
    %% Configuración de postes de entrada
    posteE1 & posteE2 & posteE3 --> tipoPosteEntrada{¿Tipo de poste de entrada?}
    
    tipoPosteEntrada -->|Estándar| posteEntradaEstandar[Poste con lector QR y documentos]
    tipoPosteEntrada -->|Avanzado| posteEntradaAvanzado[Poste con impresor QR, lector QR y documentos]
    tipoPosteEntrada -->|Premium| posteEntradaPremium[Poste doble altura con lector QR y documentos]
    
    %% Determinación de postes de salida
    evaluacionSalidas -->|1 salida| posteS1[1 Poste de salida]
    evaluacionSalidas -->|2 salidas| posteS2[2 Postes de salida]
    evaluacionSalidas -->|3+ salidas| posteS3[3+ Postes de salida]
    
    %% Configuración de postes de salida
    posteS1 & posteS2 & posteS3 --> tipoPosterSalida{¿Tipo de poste de salida?}
    
    tipoPosterSalida -->|Estándar| posteSalidaEstandar[Poste con lector QR y documentos]
    tipoPosterSalida -->|Premium| posteSalidaPremium[Poste doble altura con lector QR y documentos]
    
    %% Determinación de barreras
    posteEntradaEstandar & posteEntradaAvanzado & posteEntradaPremium --> barrerasEntrada[Barreras para entradas]
    posteSalidaEstandar & posteSalidaPremium --> barrerasSalida[Barreras para salidas]
    
    barrerasEntrada & barrerasSalida --> tipoBarrera{¿Tipo de barrera vehicular?}
    
    tipoBarrera -->|Estándar| barreraEstandar[Barrera JG-20000 - Brazo 3m]
    tipoBarrera -->|Larga| barreraLarga[Barrera JG-20000 - Brazo 4m]
    tipoBarrera -->|Extra larga| barreraExtraLarga[Barrera JG-20000 - Brazo 5m]
    
    %% Determinación de controladores/convertidores
    barreraEstandar & barreraLarga & barreraExtraLarga --> controlBarreras{¿Tipo de control?}
    
    controlBarreras -->|Básico| controlBasico[1 Conversor 232/485 por cada par entrada/salida]
    controlBarreras -->|Avanzado| controlAvanzado[1 Conversor 232/485 por cada entrada/salida]
    
    %% Determinación de detectores de masa
    controlBasico & controlAvanzado --> detectorMasa[Detector de masa metálica por cada barrera]
    
    %% Determinación de servidores y puestos de cobro
    detectorMasa --> servidorParking{¿Configuración de servidor?}
    
    servidorParking -->|Básico| servidorBasico[1 Server Parking - i3, 8GB RAM, 2 SSD]
    servidorParking -->|Redundante| servidorRedundante[2 Servers Parking con redundancia]
    
    servidorBasico & servidorRedundante --> puestoCobro{¿Puestos de cobro?}
    
    puestoCobro -->|Mínimo| cobroMinimo[1 Puesto de cobro]
    puestoCobro -->|Estándar| cobroEstandar[2 Puestos de cobro]
    puestoCobro -->|Alto volumen| cobroAltoVolumen[3+ Puestos de cobro]
    
    %% Componentes adicionales
    cobroMinimo & cobroEstandar & cobroAltoVolumen --> componentesAdicionales{¿Componentes adicionales?}
    
    componentesAdicionales -->|Control de altura| sensorAltura[Sensor de altura por entrada]
    componentesAdicionales -->|Control manual| pulsadorManual[Pulsadores de accionamiento manual]
    componentesAdicionales -->|Backup energía| upsSystem[UPS On Line 2KWA]
    componentesAdicionales -->|Todo incluido| fullComponents[Sensores + Pulsadores + UPS]
    
    %% Software y licencias
    sensorAltura & pulsadorManual & upsSystem & fullComponents --> softwareLicencias{¿Software requerido?}
    
    softwareLicencias -->|Básico| licenciaBasica[Software Winpark básico]
    softwareLicencias -->|Supervisor| licenciaSupervisor[Software Parking Supervisor/Puesto Cobro]
    softwareLicencias -->|Gestión completa| licenciaGestion[Software Country Gestión completo]
    
    %% Resultado final de componentes
    licenciaBasica & licenciaSupervisor & licenciaGestion --> listaFinalComponentes[Lista final de componentes para presupuesto]
```

## Componentes y sus características

### Postes de entrada
- **Estándar**: Poste con lector QR y documentos (MicroPDF) - ~$1,200-1,450 USD
- **Avanzado**: Poste con impresor QR, lector QR y documentos - ~$1,450-1,667 USD
- **Premium**: Poste doble altura con lector QR y documentos - ~$6,315 USD

### Postes de salida
- **Estándar**: Poste con lector QR y documentos - ~$1,050-1,598 USD
- **Premium**: Poste doble altura con lector QR y documentos - ~$6,315 USD

### Barreras vehiculares JG-20000
- **Estándar**: Brazo de 3 metros - ~$1,390-2,430 USD
- **Características**: 20,000 ciclos/día, apertura 1.8-2.5 segundos, IP55, motor 1/6 HP

### Conversores y detectores
- **Conversor 232/485**: ~$90-145 USD cada uno
- **Detector de masa metálica**: Incluido con cada barrera

### Servidores y puestos de cobro
- **Server Parking**: ~$990-2,105 USD (CPU i3, 8GB RAM, 2 SSD 240GB)
- **Puesto de cobro**: ~$1,050-2,089 USD (CPU i3, 8GB RAM, 1 SSD 240GB, lector QR/MicroPDF)

### Componentes adicionales
- **Sensor de altura**: ~$690 USD
- **Pulsador de accionamiento manual**: ~$40-65 USD
- **UPS On Line 2KWA**: ~$990-1,130 USD

### Software y licencias
- **Software Winpark básico**: ~$615-900 USD
- **Software Supervisor/Puesto Cobro**: ~$810 USD
- **Software Country Gestión**: ~$615 USD

## Instrucciones de uso

1. **Iniciar con la evaluación de entradas y salidas** para determinar la cantidad de postes necesarios
2. **Seleccionar el tipo de postes** según los requerimientos específicos
3. **Determinar las barreras** adecuadas para cada entrada/salida
4. **Configurar el control** con los conversores necesarios
5. **Dimensionar los servidores y puestos de cobro** según el volumen esperado
6. **Añadir componentes adicionales** según necesidades específicas
7. **Seleccionar el software** más adecuado
8. **Generar la lista final** de componentes para el presupuesto
