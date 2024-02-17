## Información del request de la API de pagos con tarjetas

### 1. Parámetros de la solicitud:

- **language**: El idioma en el que deseas recibir las respuestas de PayU. En este caso, "es" para español.
  
- **command**: En este caso, "SUBMIT_TRANSACTION" para enviar una transacción.

- **merchant**: Datos de la cuenta del comerciante:
  - apiKey.
  - apiLogin.

- **transaction**: Información de la transacción:
  - **order**: Detalles del pedido:
    - **accountId:** Identificador de tu cuenta en PayU.
    - **referenceCode:** Código único para identificar la transacción.
    - ***description:*** Descripción opcional de la transacción.
    - ***notifyUrl:*** URL para recibir notificaciones sobre el estado de la transacción.
    - ***additionalValues:*** Valores adicionales para la transacción.
      - TX_VALUE: Valor total de la transacción.
      - TX_TAX: Monto de impuestos asociados con la transacción.
      - TX_TAX_RETURN_BASE: Valor base para el cálculo de los impuestos de retorno.
    - ***buyer:*** Detalles del comprador.
    - ***shippingAddress:*** Dirección de envío.
  - **payer**: Detalles del pagador.
  - **creditCard**: Información de la tarjeta de crédito utilizada para el pago.
  - **extraParameters**: Parámetros adicionales para la transacción.
  - **type**: Tipo de transacción que estás realizando.
  - **paymentMethod**: Método de pago utilizado.
  - **paymentCountry**: País donde se realiza la transacción.
  - **deviceSessionId**, **ipAddress**, **cookie**, **userAgent**: Información del dispositivo y del cliente que realiza la transacción.
  
- **test**: Un indicador booleano para especificar si la transacción es una prueba (`true`) o una transacción real (`false`).

### 2. Request:

```json
{
    "language": "es",
    "command": "SUBMIT_TRANSACTION",
    "merchant": {
        "apiKey": "4Vj8eK4rloUd272L48hsrarnUA",
        "apiLogin": "pRRXKOl8ikMmt9u"
    },
    "transaction": {    
        "order": {
            "accountId": "{{account_co}}",
            "referenceCode": "{{reference_code}}",
            "description": "Payment test description",
            "language": "es",
            "signature": "{{signature}}",
            "notifyUrl": "{{confirmation_page}}",
            "additionalValues": {
                "TX_VALUE": {
                    "value": {{tx_value_co}},
                    "currency": "{{currency_co}}"
                },
                "TX_TAX": {
                    "value": 0,
                    "currency": "{{currency_co}}"
                },
                "TX_TAX_RETURN_BASE": {
                    "value": 0,
                    "currency": "{{currency_co}}"
                }
            },
            "buyer": {
                "merchantBuyerId": "1",
                "fullName": "First name and second buyer name",
                "emailAddress": "buyer_test@test.com",
                "contactPhone": "7563126",
                "dniNumber": "123456789",
                "shippingAddress": {
                    "street1": "calle 100",
                    "street2": "5555487",
                    "city": "Medellin",
                    "state": "Antioquia",
                    "country": "CO",
                    "postalCode": "000000",
                    "phone": "7563126"
                }
            },
            "shippingAddress": {
                "street1": "calle 100",
                "street2": "5555487",
                "city": "Medellin",
                "state": "Antioquia",
                "country": "CO",
                "postalCode": "0000000",
                "phone": "7563126"
            }
        },
        "payer": {
            "merchantPayerId": "1",
            "fullName": "First name and second payer name",
            "emailAddress": "payer_test@test.com",
            "contactPhone": "7563126",
            "dniNumber": "5415668464654",
            "billingAddress": {
                "street1": "calle 93",
                "street2": "125544",
                "city": "Bogota",
                "state": "Bogota DC",
                "country": "CO",
                "postalCode": "000000",
                "phone": "7563126"
            }
        },
        "creditCard": {
            "number": "4037997623271984",
            "securityCode": "321",
            "expirationDate": "2030/12",
            "name": "APPROVED"
        },
        "extraParameters": {
            "INSTALLMENTS_NUMBER": 1
        },
        "type": "AUTHORIZATION_AND_CAPTURE",
        "paymentMethod": "VISA",
        "paymentCountry": "CO",
        "deviceSessionId": "vghs6tvkcle931686k1900o6e1",
        "ipAddress": "127.0.0.1",
        "cookie": "pt1t38347bs6jc9ruv2ecpv7o2",
        "userAgent": "Mozilla/5.0 (Windows NT 5.1; rv:18.0) Gecko/20100101 Firefox/18.0"
    },
    "test": true
}
```