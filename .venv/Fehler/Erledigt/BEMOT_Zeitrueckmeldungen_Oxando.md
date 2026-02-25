Ich habe von Items eine Mail mit der folgenden Frage erhalten: wir wollen bei der KVG das Feld �Berechnungsmotiv� (BEMOT) in den Zeitr�ckmeldungen �ber einen User-Exit automatisch bef�llen.

Das gilt auch f�r R�ckmeldungen, die aus Oxando gebucht werden.

Daher die w�ssten wir gern, wie Oxando diese R�ckmeldungen verbucht. L�uft das �ber BAPI_ALM_CONF_CREATE oder setzt Ihr anderswo an?

## Mail unter Absprache mit Klaus beantwortet. Im Oxando Standard erfolgt die Verbuchung über /AXO/AM_BUS2128 (Methode POST_TIMECONF) und läuft dabei über BAPI_ALM_CONF_CREATE. 
