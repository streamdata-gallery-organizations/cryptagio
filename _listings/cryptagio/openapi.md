---
swagger: "2.0"
x-collection-name: Cryptagio
x-complete: 1
info:
  title: Cryptagio API
  description: -public--private-methodstable--thead--tr-----td-bpublic-methodsb-td----td-bprivate-methodsb-td--tr--thead--tr-----td-no-authorization-required-td----td-authorization-required-td--trtable-authorization--to-use-private-methods-you-need-to-get-your-accesssecret-key-first-on-cryptagio-comhttpscryptagio-com--after-signed-up-and-verified-visit-api-tokens-page-to-get-your-keys----p-all-requests-to-the-private-methods-require-these-headershr--table--tr-----td-bxpublickeyb-td----td-your-access-key-td--tr--tr-----td-bxtonceb-td----td-tonce-is-a-timestamp-in-integer-stands-for-microseconds-elapsed-since-unix-epoch--tonce-must-be-within-30-seconds-of-servers-current-time--each-tonce-can-only-be-used-once-td--tr--tr-----td-bxsignatureb-td----td-signature-of-the-api-request-generated-by-you-use-your-secret-key-td--tr--table--hr----signaturefor-signature-use-ed25519httped25519-cr-yp-to--sign-the-message-using-your-secret-key-and-return-a-signed-message-----signature--signmessage-secret-key-message-is-a-combination-of-requestbody-uri-and-tonce-string----message--requestbodyuritonce--table--tr-----td-irequestbodyi-td----td-requestbody-in-the-json-format--required-only-for-post-methods-td--tr--tr-----td-iurii-td----td-request-path-like-ordersmylimit50orderdesc-td--tr--tr-----td-itonce-i-td----td-timestamp-in-integer-stands-for-microseconds-elapsed-since-unix-epoch-td--tr--tablemessage-examples-p-post-message-marketethbtcsidebidamount1price0-07typelimitorders1531816217872000000-p-get-message-ordersmylimit50orderdesc1531816217872000000hr--examplesp-curl-x-post-httpsapi-cryptagio-comorders-h-accept-applicationjson-h-xtonce-1531816217872000000-h-xsignature-signature-h-xpublickey-your-access-key-h-contenttype-applicationjson-d-marketbtcethsidebidamount1price0-07typelimit-p-curl-x-get-httpsapi-cryptagio-comordersmylimit50orderdesc-h-accept-applicationjson-h-xtonce-1531816217872000000-h-xsignature-signature-h-xpublickey-your-access-key
  version: 1.0.0
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /info:
    get:
      summary: Get Info
      description: Get information..
      operationId: getInfo
      x-api-path-slug: info-get
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Info
  /ticker:
    get:
      summary: Get Ticker
      description: Get ticker of all markets..
      operationId: getTicker
      x-api-path-slug: ticker-get
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Ticker
  /trades:
    get:
      summary: Get Trades
      description: Get recent trades on market, each trade is included only once.
        Trades are sorted in reverse creation order.
      operationId: getTrades
      x-api-path-slug: trades-get
      parameters:
      - in: query
        name: from_time
        description: Filter trades by time
      - in: query
        name: from_uuid
        description: Filter trades by id
      - in: query
        name: limit
        description: Limit the number of returned trades
      - in: query
        name: market
        description: Filter trades by market
      - in: query
        name: order
        description: If set, returned orders will be sorted in specific order
      - in: query
        name: side
      - in: query
        name: to_time
        description: Filter trades by time
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Trades
  /trades/my:
    get:
      summary: Get My Trades
      description: Trades are sorted in reverse creation order.
      operationId: getTradesMy
      x-api-path-slug: tradesmy-get
      parameters:
      - in: query
        name: from_time
        description: Filter trades by time
      - in: query
        name: from_uuid
        description: Filter trades by id
      - in: query
        name: limit
        description: Limit the number of returned trades
      - in: query
        name: market
        description: Filter trades by market
      - in: query
        name: order
        description: If set, returned orders will be sorted in specific order
      - in: query
        name: side
      - in: query
        name: to_time
        description: Filter trades by time
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Trades
      - My
  /balances:
    get:
      summary: Get Balances
      description: Get user balances..
      operationId: getBalances
      x-api-path-slug: balances-get
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Balances
  /orders/my:
    get:
      summary: GetMy  Orders
      description: Trades are sorted in reverse creation order.
      operationId: getOrdersMy
      x-api-path-slug: ordersmy-get
      parameters:
      - in: query
        name: from_time
        description: Filter trades by time
      - in: query
        name: from_uuid
        description: Filter orders by id
      - in: query
        name: limit
        description: Limit the number of returned trades
      - in: query
        name: market
        description: Filter orders by market
      - in: query
        name: order
        description: If set, returned orders will be sorted in specific order
      - in: query
        name: side
        description: Filter orders by side
      - in: query
        name: status
        description: Filter orders by status
      - in: query
        name: to_time
        description: Filter trades by time
      - in: query
        name: type
        description: Filter orders by type
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Orders
      - My
  /orders:
    post:
      summary: Post Orders
      description: Accepts an array of JSON objects.
      operationId: postOrders
      x-api-path-slug: orders-post
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Orders
  /orders/cancel:
    post:
      summary: Post Orders Cancel
      description: Accepts JSON object. Cancels all orders if no parameters are passed.
      operationId: postOrdersCancel
      x-api-path-slug: orderscancel-post
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Orders
      - Cancel
  /orders/{uuid}:
    delete:
      summary: Delete Orders
      description: Cancel order by uuid..
      operationId: deleteOrdersUu
      x-api-path-slug: ordersuuid-delete
      parameters:
      - in: path
        name: uuid
      responses:
        200:
          description: OK
      tags:
      - Blockchain
      - Orders
      - Uuid
---