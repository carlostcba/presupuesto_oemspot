# Flujo Visual del Proceso de Presupuestación

El siguiente diagrama muestra el flujo completo del proceso de presupuestación para sistemas de estacionamiento ParkingYa:

```mermaid
flowchart TD
    Start([INICIO]) --> Fase1[Fase 1: Primer contacto con el cliente]
    Fase1 --> Fase2[Fase 2: Recopilación de información básica]
    
    subgraph Evaluación["EVALUACIÓN TÉCNICA"]
        Fase2 --> Fase3[Fase 3: Relevamiento de infraestructura]
        Fase3 --> Fase4[Fase 4: Evaluación de necesidades operativas]
        Fase4 --> Fase5[Fase 5: Visita técnica]
    end
    
    subgraph Presupuesto["ELABORACIÓN DEL PRESUPUESTO"]
        Fase5 --> Fase6[Fase 6: Determinación de componentes]
        Fase6 --> Fase7[Fase 7: Cálculo del costo de equipamiento]
        Fase7 --> Fase8[Fase 8: Determinación del esquema comercial]
        Fase8 --> Fase9[Fase 9: Incorporación de componentes adicionales]
    end
    
    subgraph Propuesta["GENERACIÓN DE LA PROPUESTA"]
        Fase9 --> Fase10[Fase 10: Elaboración del documento]
        Fase10 --> Fase11[Fase 11: Revisión interna]
        Fase11 --> Fase12[Fase 12: Presentación al cliente]
    end
    
    subgraph Cierre["SEGUIMIENTO Y CIERRE"]
        Fase12 --> Decision{¿Cliente acepta?}
        Decision -->|No| Fase13[Fase 13: Ajustes al presupuesto]
        Fase13 --> Fase12
        Decision -->|Sí| Fase14[Fase 14: Cierre y formalización]
    end
    
    Fase14 --> End([FIN - IMPLEMENTACIÓN])
    
    classDef fase fill:#f9f9f9,stroke:#333,stroke-width:1px;
    class Fase1,Fase2,Fase3,Fase4,Fase5,Fase6,Fase7,Fase8,Fase9,Fase10,Fase11,Fase12,Fase13,Fase14 fase;
    
    classDef decision fill:#fffdf9,stroke:#333,stroke-width:1px;
    class Decision decision;
    
    classDef endpoint fill:#d4f9d4,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5;
    class Start,End endpoint;
```

## Descripción de las fases

### Preparación inicial
- **Fase 1**: Primer contacto con el cliente
- **Fase 2**: Recopilación de información básica

### Evaluación técnica
- **Fase 3**: Relevamiento de infraestructura
- **Fase 4**: Evaluación de necesidades operativas
- **Fase 5**: Visita técnica (opcional pero recomendada)

### Elaboración del presupuesto
- **Fase 6**: Determinación de componentes necesarios
- **Fase 7**: Cálculo del costo de equipamiento
- **Fase 8**: Determinación del esquema comercial
- **Fase 9**: Incorporación de componentes adicionales

### Generación de la propuesta
- **Fase 10**: Elaboración del documento de presupuesto
- **Fase 11**: Revisión interna
- **Fase 12**: Presentación al cliente

### Seguimiento y cierre
- **Fase 13**: Ajustes al presupuesto (si es necesario)
- **Fase 14**: Cierre y formalización
