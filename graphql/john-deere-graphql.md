# John Deere GraphQL Schema

## Overview

This conceptual GraphQL schema represents the John Deere precision agriculture and equipment API domain. John Deere's developer platform (https://developer.deere.com/) exposes machine telemetry, field operations, fleet management, and precision agriculture data through its Operations Center ecosystem.

The schema below models the key entities surfaced by the John Deere REST API and maps them into a GraphQL type system to enable graph-style querying across machines, fields, organizations, and agronomic data.

## Schema Source

- API Portal: https://developer.deere.com/
- GitHub Organization: https://github.com/JohnDeere
- Authentication: OAuth 2.0

## Key Domains

### Equipment and Fleet

John Deere's connected equipment platform exposes machine-level telemetry including engine hours, fuel usage, fault codes, and GPS-based machine location. Machines are grouped into fleets owned by organizations.

### Field Operations

Field boundaries, crop zones, and management zones define the agronomic geography. Field operations capture what was done in each field — planting, spraying, tillage, and harvesting activities with as-applied data.

### Precision Agriculture

Prescriptions define variable-rate application plans for seeding and chemical inputs. Yield maps, as-applied maps, and prescription maps represent the spatial layer outputs of precision ag workflows. Soil data and satellite imagery enrich agronomic decision-making.

### Telemetry and Health

TelematicsRecord entries stream engine RPM, speed, fuel level, and position at regular intervals. EngineHealth, FaultCode, and MaintenanceAlert types capture equipment condition and service requirements.

### Weather and Environment

FieldWeather and WeatherData types expose localized weather conditions tied to field locations. SoilMoisture and Irrigation types support water management workflows.

## Authentication

All queries require a valid OAuthToken obtained through the John Deere OAuth 2.0 authorization flow. Tokens are scoped per organization and control access to machine data, field data, and operations data separately.

## Types Summary

The schema defines 62 named types covering:

- Equipment: Machine, MachineInfo, Equipment, EquipmentDetails, Fleet, EngineHours, FuelUsage, MachineLocation, OperatingHour, EquipmentSync, MachineAlert
- Telemetry and Health: TelematicsRecord, EngineHealth, FaultCode, MaintenanceAlert, ServiceRecord
- Field and Agronomic Geography: Field, FieldBoundary, CropZone, ManagementZone, Boundary, GeoPoint, GeoPolygon
- Field Operations: FieldOperation, FieldActivity, HarvesterData, PlantingData, SprayingData, TillageData
- Precision Agriculture: Prescription, SeedingPrescription, ApplicationPrescription, PrescriptionMap, Variety, Seed, PrecisionAg
- Soil and Yield: SoilData, YieldData, YieldMap, AsAppliedMap, SoilMoisture
- Imagery and Weather: SatelliteImagery, WeatherData, FieldWeather
- Irrigation: Irrigation, IrrigationZone
- Organization and Auth: Organization, APIClient, OAuthToken
- Enumerations: MachineStatus, OperationType, CropType, FaultSeverity, PrescriptionType, SoilTextureClass, WeatherCondition, IrrigationMethod, ImagerySource
- Queries and Mutations: Query root, Mutation root
