# SIGE Theory Project: Hotel Booking Demand Dataset

Este proyecto analiza el dataset de Kaggle: [Hotel Booking Demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand).  
Construimos un pipeline completo para preprocesar los datos y aplicar técnicas de clasificación.

---

## Diccionario de Variables

| **Columna**                    | **Descripción**                                                                                                   | **Valores / Ejemplo**                                                                                      |
|--------------------------------|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| **hotel**                      | Tipo de hotel reservado.                                                                                         | `City Hotel` (urbano), `Resort Hotel` (vacacional)                                                         |
| **is_canceled**                | Indica si la reserva fue cancelada.                                                                              | `0`: No cancelada, `1`: Cancelada                                                                          |
| **lead_time**                  | Días entre la reserva y el check-in.                                                                             | `100` (reservó 100 días antes)                                                                             |
| **arrival_date_year**          | Año del check-in.                                                                                                | `2015`, `2016`, `2017`                                                                                     |
| **arrival_date_month**         | Mes del check-in (texto, capitalizado).                                                                          | `January`, `February`, ..., `December`                                                                     |
| **arrival_date_week_number**   | Semana del año de llegada.                                                                                       | `1` a `52` (o `53`)                                                                                        |
| **arrival_date_day_of_month**  | Día del mes de llegada.                                                                                          | `1` a `31`                                                                                                 |
| **stays_in_weekend_nights**    | Noches de fin de semana (viernes y sábado).                                                                      | `2` (ejemplo: viernes a domingo)                                                                           |
| **stays_in_week_nights**       | Noches entre semana (lunes a jueves).                                                                            | `2` (ejemplo: miércoles a viernes)                                                                         |
| **adults**                     | Número de adultos (≥ 18 años).                                                                                   | `2`                                                                                                        |
| **children**                   | Número de niños (< 18 años).                                                                                     | `1`, `0` (NaN se reemplaza por 0)                                                                          |
| **babies**                     | Número de bebés (< 2 años).                                                                                      | `0`                                                                                                        |
| **meal**                       | Plan de comidas contratado.                                                                                      | `BB` (desayuno), `HB` (media pensión), `FB` (pensión completa), `SC` (solo alojamiento)                   |
| **country**                    | Código de país (ISO-3166 alpha-3).                                                                               | `PRT` (Portugal), `GBR` (Reino Unido), `USA` (Estados Unidos)                                              |
| **market_segment**             | Canal de captación de la reserva.                                                                                | `Direct`, `Corporate`, `Online TA`, `Offline TA/TO`, `Groups`, `Complementary`                             |
| **distribution_channel**       | Canal específico de confirmación.                                                                                | `Direct`, `TA/TO`, `Corporate`, `GDS`                                                                      |
| **is_repeated_guest**          | Si el cliente ya se alojó antes.                                                                                 | `0`: No, `1`: Sí                                                                                           |
| **previous_cancellations**     | Reservas canceladas previamente por el cliente.                                                                  | `1`                                                                                                        |
| **previous_bookings_not_canceled** | Reservas previas no canceladas.                                                                             | `2`                                                                                                        |
| **reserved_room_type**         | Tipo de habitación reservada (código letra).                                                                     | `A`, `B`, ..., `L`, `P`                                                                                    |
| **assigned_room_type**         | Tipo de habitación asignada al check-in (código letra).                                                          | `A`, `B`, ..., `L`, `P`                                                                                    |
| **booking_changes**            | Número de modificaciones a la reserva antes del check-in.                                                        | `0` (sin cambios), `2` (dos cambios)                                                                       |
| **deposit_type**               | Tipo de depósito exigido.                                                                                        | `No Deposit`, `Non Refund`, `Refundable`                                                                   |
| **agent**                      | Código de agencia/agente que realizó la reserva.                                                                 | `9`, `304`, `NaN` (directa)                                                                                |
| **company**                    | Código de empresa (cuenta corporativa).                                                                          | `40`, `171`, `NaN` (personal)                                                                              |
| **days_in_waiting_list**       | Días en lista de espera.                                                                                         | `0` (sin espera), `3` (esperó 3 días)                                                                      |
| **customer_type**              | Tipo de cliente según uso de la habitación.                                                                      | `Transient`, `Contract`, `Transient-Party`, `Group`                                                        |
| **adr**                        | Tarifa diaria promedio pagada (Average Daily Rate).                                                              | `adr = ingresos totales / número de noches de estancia`                                                    |
| **required_car_parking_spaces**| Plazas de aparcamiento solicitadas.                                                                              | `0`, `1`, ...                                                                                              |
| **total_of_special_requests**  | Número de peticiones especiales realizadas.                                                                      | `0` (ninguna), `2` (dos solicitudes)                                                                       |
| **reservation_status**         | Estado final de la reserva.                                                                                      | `Canceled`, `Check-Out`, `No-Show`                                                                         |
| **reservation_status_date**    | Fecha de actualización del estado de la reserva (YYYY-MM-DD).                                                    | `2017-09-14`                                                                                               |

---

## Notas y Observaciones

- **market_segment** vs **distribution_channel**:  
    - *market_segment* agrupa canales de forma general (ej. "Online TA" para todas las OTAs).
    - *distribution_channel* indica el canal específico (ej. Booking.com, Amadeus).

- **adr**:  
    Puede ser negativo o cero si hubo descuentos o reembolsos.

- **Valores NaN**:  
    En columnas como `children`, `agent` o `company`, NaN indica ausencia de valor (ej. reserva directa o personal).

---

## Ejemplos de Peticiones Especiales

- Cama supletoria
- Habitación cerca del ascensor
- Habitación silenciosa
- Ayuda para celíacos


