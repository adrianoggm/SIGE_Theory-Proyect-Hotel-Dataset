# SIGE_Theory-Proyect-Hotel-Dataset
We are conducting an analysis using the Kaggle dataset available at this link https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand  Our project involves building a comprehensive pipeline to preprocess the data and implement various classification techniques.

hotel

Qué almacena: El tipo de hotel al que se refiere la reserva.

Valores posibles:

"City Hotel": Hotel urbano (ciudad).

"Resort Hotel": Hotel de tipo resort (vacacional).

is_canceled

Qué almacena: Indica si la reserva fue cancelada o no.

Valores:

0: la reserva no se canceló (se mantuvo activa).

1: la reserva sí se canceló.

lead_time

Qué almacena: Número de días entre la fecha en la que se hizo la reserva y la fecha de llegada (check‐in).

Ejemplo: Si alguien reservó con 100 días de antelación, aquí se guardaría 100.

arrival_date_year

Qué almacena: Año del check‐in (llegada) reservado.

Ejemplo: 2015, 2016, 2017…

arrival_date_month

Qué almacena: Mes del check‐in, en texto (con la primera letra en mayúscula).

Valores posibles:

"January", "February", "March", …, "December".

arrival_date_week_number

Qué almacena: Número de semana del año en la que se produce la llegada.

Formato: Un entero entre 1 y 52 (o 53 en años con 53 semanas).

arrival_date_day_of_month

Qué almacena: Día del mes en que se realiza el check‐in (1–31).

stays_in_weekend_nights

Qué almacena: Cantidad de noches que el huésped se quedará en el hotel durante el fin de semana (viernes y sábado).

Ejemplo: Si entra un viernes y sale el domingo, habría 2 noches en fin de semana.

stays_in_week_nights

Qué almacena: Cantidad de noches que el huésped va a permanecer en el hotel durante días laborables (lunes a jueves).

Ejemplo: Si entra un miércoles y sale un viernes, serían 2 noches en día laborable.

adults

Qué almacena: Número de huéspedes adultos (≥ 18 años) incluidos en la reserva.

children

Qué almacena: Número de niños (usualmente < 18 años) incluidos en la reserva.

Importante: A veces en el CSV original aparecen valores vacíos (NaN) si no se especificó. Normalmente se reemplaza con 0 si se asume que no hay niños.

babies

Qué almacena: Número de bebés (muy pequeños, < 2 años) incluidos en la reserva.

meal

Qué almacena: Plan de comida contratado para cada huésped.

Valores típicos:

BB (Bed & Breakfast): Alojamiento + desayuno.

HB (Half Board): Alojamiento + desayuno + cena.

FB (Full Board): Alojamiento + desayuno + comida + cena.

SC (Self Catering): Solo alojamiento, sin comidas incluidas.

country

Qué almacena: Código de país (ISO-3166 alpha-3, tres letras) de procedencia del cliente.

Ejemplo:

PRT = Portugal

GBR = Reino Unido

USA = Estados Unidos, etc.

market_segment

Qué almacena: Segmento de mercado o canal de captación, es decir, a través de qué vía llegó la reserva.

Valores posibles (ejemplos habituales):

Direct: Reserva hecha directamente en la web del hotel.

Corporate: Reserva realizada por una empresa a través de un acuerdo corporativo.

Online TA: Agencia de viajes online (por ejemplo, Booking.com, Expedia).

Offline TA/TO: Agencia de viajes “física” u offline (tour operator).

Groups: Grupos de más de 10 personas.

Complementary: Reserva complementaria (ej. invitados del propio hotel).

… y otros subsegmentos.

distribution_channel

Qué almacena: Canal específico a través del cual se confirmó la reserva.

Valores típicos:

Direct: Desde la web del hotel o teléfono.

TA/TO: Agencia de viajes online u offline.

Corporate: A través de un acuerdo de empresa.

GDS (Global Distribution System): Plataformas globales como Amadeus, Sabre, Travelport.

Otros.

Diferencia con “market_segment”:

El market_segment agrupa de forma más amplia (ej. “Online TA” para todas las OTAs).

El distribution_channel precisa el canal preciso (Booking.com, Expedia, Amadeus, etc.).

is_repeated_guest

Qué almacena: Indica si el cliente ya se había alojado antes en el hotel (incluso si fue en un hotel distinto del mismo grupo).

Valores:

0: No es huésped recurrente (primera reserva).

1: Sí es huésped recurrente.

previous_cancellations

Qué almacena: Cantidad de reservas canceladas previamente por este cliente.

Ejemplo: Si en el pasado alguien reservó dos veces y canceló una de ellas, aquí sería 1.

previous_bookings_not_canceled

Qué almacena: Cantidad de reservas no canceladas (completadas) previamente por el cliente.

reserved_room_type

Qué almacena: Tipo de habitación que el huésped reservó originalmente (código de una letra).

Valores típicos (ejemplos de letras que aparecen en el dataset original):

A, B, C, …, L, P (cada letra corresponde a una categoría de habitación).

assigned_room_type

Qué almacena: Tipo de habitación que finalmente se le asignó en el check‐in (también con un código de letra).

Observación:

Si en el momento de llegada no había disponibilidad del “reserved_room_type”, a veces se reasigna otra (por eso puede diferir de reserved_room_type).

Si coincide, el valor será la misma letra, indicando que sí obtuvo la habitación original.

booking_changes

Qué almacena: Número de veces que el cliente modificó la reserva antes del check‐in.

Ejemplo: Si hizo cambio de fechas, cambio de número de huéspedes, upgrade de habitación, etc., cada uno cuenta como un “booking change”. Un cero (0) significa que no hubo modificaciones.

deposit_type

Qué almacena: Tipo de depósito que se exigió al cliente para garantizar la reserva.

Valores:

No Deposit: No se exigió ningún anticipo.

Non Refund: No reembolsable (se retiene todo el importe aunque se cancele).

Refundable: Depósito reembolsable si se cancela antes de cierta fecha.

agent

Qué almacena: Código numérico que identifica a la agencia (o agente) que realizó la reserva, en caso de que no haya sido directa.

Ejemplo:

9 → agencia interna del propio hotel.

304 → identificación de una agencia OTA concreta.

NaN → si la reserva fue “directa” (no intervino ningún agente).

company

Qué almacena: Código numérico de la empresa (corporate account) cuando la reserva se hizo a través de un acuerdo corporativo.

Ejemplo:

40 → Avis Budget Group.

171 → Deutsche Bank.

NaN → si no hay empresa asociada (reserva personal).

days_in_waiting_list

Qué almacena: Número de días que el cliente esperó en lista de espera para poder conseguir la habitación.

Interpretación:

Un valor 0 indica que no esperó en lista de espera (hubo disponibilidad inmediatamente).

Un valor positivo muestra cuántos días estuvo aguardando antes de que se confirmara la reserva o se cancelara por falta de espacio.

customer_type

Qué almacena: Tipo de cliente según la forma en que se usaba la habitación.

Valores posibles:

Transient: Reserva individual (no grupal).

Contract: Reserva bajo contrato (por ejemplo, tarifa fija anual negociada).

Transient-Party: Grupos pequeños (menos de 10 personas) con tarifa especial para “fiestas/reuniones”.

Group: Grupos grandes (10 o más personas).

adr

Qué almacena: “Average Daily Rate” o tarifa diaria promedio pagada por el cliente (en la moneda local, normalmente euros).

Cálculo:

adr
=
total de ingresos (room_nights)
n
u
ˊ
mero de noches de estancia
adr= 
n 
u
ˊ
 mero de noches de estancia
total de ingresos (room_nights)
​
 
Donde “room_nights” son noches habitadas (fines de semana + laborables) multiplicadas por tarifa.

Nota: A veces hay valores “negativos” o “cero” si hubo descuentos o cancelaciones con reembolso parcial.

required_car_parking_spaces

Qué almacena: Número de plazas de aparcamiento solicitadas por el cliente (0 si no solicitó).

total_of_special_requests

Qué almacena: Cuántas peticiones especiales hizo el cliente al hacer la reserva.

Ejemplos de “special requests”:

“cama supletoria”

“cerca del ascensor”

“habitación silenciosa”

“ayuda para celiacos”

Si aquí hay 0, significa que no realizó ninguna solicitud adicional.

reservation_status

Qué almacena: Estado final de la reserva.

Valores posibles:

Canceled: Reserva cancelada.

Check-Out: El cliente llegó y salió (estancia completada).

No-Show: El cliente no se presentó (no llegó a registrarse).

reservation_status_date

Qué almacena: Fecha en la que se actualizó por última vez el estado de la reserva.

Formato: YYYY-MM-DD.

Interpretación:

Si reservation_status = “Canceled”, esta columna indica la fecha en que el huésped canceló.

Si reservation_status = “Check-Out”, es la fecha de salida (checkout).

Si reservation_status = “No-Show”, es la fecha en que se marcó como no presentado.