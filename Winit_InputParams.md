## 海外仓API（oswh）

### 商品

#### 查询商品

| 名称      | 类型        | 必填 | 说明                                       | 示例                |
| :-------- | :---------- | :--- | :----------------------------------------- | :------------------ |
| skuCode   | String(255) | N    | 商品编码SKU 模糊搜索                       | auto_sku22          |
| startTime | String(20)  | N    | 商品注册开始时间 格式：YYYY-MM-DD HH:MM:SS | 2019-08-01 00:00:00 |
| endTime   | String(20)  | N    | 商品注册结束时间 格式：YYYY-MM-DD HH:MM:SS | 2019-08-07 00:00:00 |

#### 查询商品审核状态

| 名称              | 类型        | 必填 | 说明                                                         | 示例                |
| :---------------- | :---------- | :--- | :----------------------------------------------------------- | :------------------ |
| skuCode           | String(100) | N    | 商品编码                                                     | POA0001             |
| name              | String(100) | N    | 商品品名(商品英文名）                                        | Shoes               |
| country           | String(100) | N    | 进口国家二字码                                               | CN                  |
| importCountryCode | String(100) | Y    | 进口国家二字码                                               | US                  |
| importStartTime   | String(50)  | N    | 注册商品开始时间 入参格式:YYYY-MM-DD HH:MM:SS                | 2018-05-01 00:00:01 |
| importEndTime     | String(50)  | N    | 注册商品结束时间 入参格式:YYYY-MM-DD HH:MM:SS                | 2019-07-01 23:59:59 |
| keyword           | String(100) | N    | 关键字字段 Name：商品名称 Skucode：商品编码                  | name                |
| keywordValue      | String(100) | Y    | 关键字查询值                                                 |                     |
| status            | String(255) | N    | 商品审核状态 DR:待维护 PD:已发布 CO:维护完成 BK:退回 WSA:验证中 | DR                  |

#### 查询商品的单品条码及其状态

| 名称          | 类型        | 必填 | 说明                                                         | 示例                |
| :------------ | :---------- | :--- | :----------------------------------------------------------- | :------------------ |
| skuCode       | String(255) | Y    | 商品编码                                                     | LCD-IP5-01          |
| specification | String(255) | N    | 商品规格                                                     | 红色                |
| barcode       | String(255) | N    | 单品条码                                                     | S000000000123456789 |
| status        | String(255) | N    | 单品状态 准备中：INIT； 在途：ON_ORDER； 待发：WAITING_OUTBOUND； 可用：USABLE； 待销毁：WAITING_DESTRUCTION； 丢失确认中：LOST_CONFIRMING； 已丢失：LOST； 已销毁：DESTRUCTION； 已出库：OUTBOUND； 已拣选：PICKED； 已打包：PACKED； 拣选完成：PKC； 海外已拆包：SPLIT； 入库丢失：LOST_INBOUND； | INIT                |



### 库存

#### 查询总库存

| 名称              | 类型      | 必填 | 说明                                                         | 示例    |
| :---------------- | :-------- | :--- | :----------------------------------------------------------- | :------ |
| warehouseID       | String()  | Y    | 仓库ID，[点击查询仓库ID](http://developer.winit.com.cn/tool/logistic.html) | 1000008 |
| warehouseCode     | String()  | O    | 仓库Code，[点击查询仓库Code](http://developer.winit.com.cn/tool/logistic.html) | DE0001  |
| isActive          | String(1) | N    | 商品是否有效                                                 | Y/N     |
| inReturnInventory | String(1) | N    | 退货库存                                                     | Y/N     |

#### 查询分类库存

| 名称             | 类型       | 必填 | 说明                                                         | 示例   |
| ---------------- | ---------- | ---- | ------------------------------------------------------------ | ------ |
| warehouseCodes   | String(20) | Y    | 仓库编码, 示例：美西仓：US0001开通仓群时，请传主仓           | US0001 |
| serviceType      | String(30) | N    | 业务用途类型，2B,2C为空默认2C，                              | 2C     |
| merchandiseCode  | String(40) | N    | 商品编码，后模糊查询                                         |        |
| merchandiseSerno | String(20) | N    | 商品条码                                                     |        |
| provideChannel   | String(30) | N    | 供应渠道， 比如：货主编码, 开启供应渠道管理时必填，未开通时忽略传入值 |        |
| merchandiseGrade | String(30) | N    | 商品等级，为空默认良品良品：GOOD不良品：DEFECTIVE            | GOOD   |
| salesChannel     | String(30) | N    | 销售渠道                                                     |        |
| organization     | String(30) | N    | 组织，为空时默认无, 开启按组织管理库存必填                   |        |
| startTime        | String(20) | Y    | 库存变更结束时间，用于筛选有变更的数据，格式 2020-01-01 00:00:00,必须和开始时间配合使用，建议每次查询范围一天 |        |
| endTime          | String(20) | Y    | 库存变更结束时间，用于筛选有变更的数据，格式 2020-01-01 00:00:00,必须和开始时间配合使用，建议每次查询范围一天 |        |

#### 查询总库存（含DOI）

| 名称          | 类型          | 必填 | 说明                                                         | 示例               |
| :------------ | :------------ | :--- | :----------------------------------------------------------- | :----------------- |
| DOITier       | String()      | N    | DOI层级： 1：30以下 2：30-60 3：60-90 4：90以上              | 1                  |
| inventoryType | String（10）  | Y    | 库存类型：Country：国家，Warehouse：仓库                     | Country            |
| isActive      | String（1）   | N    | 商品是否有效,Y/N                                             | Y                  |
| productCode   | String（510） | N    | 商品编码                                                     | SKU1               |
| name          | String（255） | N    | 商品名称                                                     | MM                 |
| warehouseId   | String()      | Y    | 仓库ID，[点击查询仓库ID](http://developer.winit.com.cn/tool/logistic.html) | 1000008            |
| warehouseCode | String()      | N    | 仓库Code，[点击查询仓库Code](http://developer.winit.com.cn/tool/logistic.html) | DE0001             |
| startTime     | String(20)    | N    | 库存变更开始时间 开始和结束时间跨度不能超过24小时            | 2020-01-01 00:00:0 |
| endTime       | String(20)    | N    | 库存变更结束时间 开始和结束时间跨度不能超过24小时            | 2020-01-01 00:00:0 |

#### 查询仓租单明细

| 名称                | 类型        | 必填 | 说明                                                         | 示例 |
| :------------------ | :---------- | :--- | :----------------------------------------------------------- | :--- |
| merchandiseCode     | string(255) | N    | 商品编码                                                     |      |
| merchandiseBarcode  | string(255) | N    | 商品条码                                                     |      |
| WarehousereceiptNum | string(255) | O    | 海外仓储收费单号                                             |      |
| warehouseCode       | String(100) | N    | 海外仓编码 通过接口[queryWarehouse](http://developer.winit.com.cn/document/detail/id/43.html)查询得到出参：warehouseCode |      |
| startTime           | String(50)  | O    | 仓租开始日期 格式：YYYY-MM-DD                                |      |
| endTime             | String(50)  | O    | 仓租结束日期 格式：YYYY-MM-DD                                |      |

#### 库存流水查询

| 名称          | 类型         | 必填 | 说明                                                         | 示例       |
| :------------ | :----------- | :--- | :----------------------------------------------------------- | :--------- |
| skuCode       | String(120)  | Y    | 商品编码                                                     | auto_sku22 |
| specification | varchar(255) | N    | 商品规格                                                     | 1000008    |
| warehouseCode | varchar(50)  | Y    | 仓库编码                                                     | DE0001     |
| docType       | varchar(30)  | N    | 订单类型 入库：INBOUND 出库：OUTBOUND 调整：ADJUSTMENT 调拨出库：ALLOCATION_OUT 调拨入库：ALLOCATION_IN 退货入库：INBOUND_RETURN 直发入库：INBOUND_OVERSEAS | INBOUND    |
| startDate     |              | Y    | 起始日期                                                     | 2020-12-01 |
| endDate       |              | Y    | 截止日期                                                     | 2020-01-01 |



### 入库

#### 查询头程服务

| 名称        | 类型         | 必填 | 说明                                                         | 示例   |
| :---------- | :----------- | :--- | :----------------------------------------------------------- | :----- |
| productType | String（20） | Y    | 产品类型：OW0101-标准海外仓入库OW0102-直发国内验入库OW0103-直发海外验入库 | OW0101 |

#### 查询验货/目的仓

| 名称                    | 类型       | 必填 | 说明                                                         | 示例       |
| :---------------------- | :--------- | :--- | :----------------------------------------------------------- | :--------- |
| winitProductCode        | String(50) | Y    | Winit产品编码                                                | OW01010382 |
| warehouseType           | String(50) | Y    | 验货仓：INSJ 目的仓：DEST                                    | INSJ       |
| orderType               | String(50) | Y    | 订单类型编码 SD-标准海外仓入库 DW-直发海外验入库 DI-直发国内验入库 | SD         |
| inspectionWarehouseCode | String(50) | N    | 验货仓编码 当warehouseType=DEST时，必填                      | SH0001     |

#### 查询入库可选商品

| 名称                     | 类型       | 必填 | 说明                                                         | 示例       |
| :----------------------- | :--------- | :--- | :----------------------------------------------------------- | :--------- |
| customerCode             | String(50) | Y    | 客户编码 客户在WINIT的唯一编码,卖家可以进入[万邑联-个人中心-系统设置-我的资料查询"Winit Account ID"](https://seller.winit.com.cn/UserCenter/userinfo) | 1000019    |
| firstLegType             | String(20) | Y    | 头程类型： WC-Winit承运 NS-直发                              | WC         |
| winitProductCode         | String(50) | Y    | WINIT产品编码 取接口[winit.wh.pms.getWinitProducts](http://developer.winit.com.cn/document/detail/id/28.html)中的productCode | OW01010382 |
| destinationWarehouseCode | String(50) | Y    | 目的仓编码 取接口[winit.pms.getWarehouseList](http://developer.winit.com.cn/document/detail/id/29.html)中的warehouseCode | US00       |

#### 查询物流计划

| 名称                     | 类型         | 必填 | 说明                                                         | 示例       |
| :----------------------- | :----------- | :--- | :----------------------------------------------------------- | :--------- |
| winitProductCode         | String（50） | Y    | WINIT产品编码                                                | OW01010382 |
| inspectionWarehouseCode  | String(50)   | Y    | 验货仓编码 通过接口[winit.pms.getWarehouseList](http://developer.winit.com.cn/document/detail/id/29.html)（查询验货/目的仓）返回出参warehouseCode | SZ0001     |
| destinationWarehouseCode | String(50)   | Y    | 目的仓编码 通过接口[winit.pms.getWarehouseList](http://developer.winit.com.cn/document/detail/id/29.html)（查询验货/目的仓）返回出参warehouseCode | US0001     |

#### 查询进口报关-IOR规则

| 名称             | 类型       | 必填 | 说明         | 示例       |
| :--------------- | :--------- | :--- | :----------- | :--------- |
| endWarehouseCode | String(40) | Y    | 目的仓库编码 | US0001     |
| productCode      | String(32) | Y    | 产品编码     | OW01010343 |

#### 查询进/出口供应商

| 名称        | 类型       | 必填 | 说明                                                   | 示例 |
| :---------- | :--------- | :--- | :----------------------------------------------------- | :--- |
| countryCode | String(50) | Y    | 国家编码： 出口商：CN 进口商：目的仓所在的国家二字简码 | US   |
| vendorType  | String(50) | Y    | 类型： IOR-进口商 EOR-出口商                           | IOR  |

#### 查询发货供应商

| 名称        | 类型       | 必填 | 说明                          | 示例     |
| :---------- | :--------- | :--- | :---------------------------- | :------- |
| shipperType | String(50) | Y    | 承运人类型: CUSTOMER-自发物流 | CUSTOMER |

#### 查询入库单（列表）

| 名称                     | 类型       | 必填 | 说明                                                         | 示例       |
| :----------------------- | :--------- | :--- | :----------------------------------------------------------- | :--------- |
| orderType                | String(50) | N    | 订单类型 SD-标准海外仓入库 DW-直发海外验入库 DI-直发国内验入库 | SD         |
| destinationWareHouseCode | String(50) | N    | 目的仓编码 取[[查询验货/目的仓\]](http://developer.winit.com.cn/document/detail/id/29.html)仓库编码 | US0001     |
| inspectionWareHouseCode  | String(50) | N    | 验货仓编码 取[[查询验货/目的仓\]](http://developer.winit.com.cn/document/detail/id/29.html)仓库编码 | SZ0001     |
| orderCreateDateEnd       | String(50) | N    | 结束下单日期                                                 | 2016-09-09 |
| orderCreateDateStart     | String(50) | N    | 开始下单日期                                                 | 2016-10-09 |
| winitProductCode         | String(50) | Y    | WINIT产品编码 取[[查询头程服务\]](http://developer.winit.com.cn/document/detail/id/28.html)的Winit产品编码 |            |

#### 查询入库单详情

| 名称             | 类型       | 必填 | 说明                                        | 示例         |
| :--------------- | :--------- | :--- | :------------------------------------------ | :----------- |
| orderNo          | String(50) | Y    | WINIT订单号                                 | WI9900001290 |
| isIncludePackage | String(10) | N    | 返回结果是否包含包裹信息。Y-是,N-否,默认N。 | Y            |

#### 查询入库单费用

| 名称                 | 类型     | 必填 | 说明           | 示例           |
| :------------------- | :------- | :--- | :------------- | :------------- |
| businessDocumentNo   | String() | Y    | 海外仓入库单号 | WI9900046392   |
| destinationWarehouse | String() | N    | 目的海外仓名称 | BEMO Warehouse |
| orderDateFrom        | Date     | N    | 查询开始日期   | 2018-01-16     |
| orderDateTo          | Date     | N    | 查询截止日期   | 2018-05-23     |

#### 查询入库轨迹

| 名称    | 类型       | 必填 | 说明     | 示例         |
| :------ | :--------- | :--- | :------- | :----------- |
| orderNo | String(50) | Y    | 入库单号 | WI9900001722 |

#### 查询出库单（列表）

| 名称                 | 类型       | 必填 | 说明                                                         | 示例 |
| :------------------- | :--------- | :--- | :----------------------------------------------------------- | :--- |
| warehouseId          | String()   | N    | 海外仓仓库Id                                                 |      |
| outboundOrderNum     | String()   | N    | 海外仓出库单号                                               |      |
| sellerOrderNo        | String()   | N    | 卖家订单号（自定义）                                         |      |
| trackingNo           | String()   | N    | 快递单号                                                     |      |
| receiverName         | String()   | N    | 收件人姓名                                                   |      |
| bookingOperator      | String()   | N    | winit客户名称                                                |      |
| productValue         | String()   | N    | 产品编码                                                     |      |
| productName          | String()   | N    | 产品名称                                                     |      |
| productSku           | String()   | N    | 商品SKU                                                      |      |
| shareOrderType       | String()   | N    | 是否共享订单（已停用） 0：不包含共享信息 1：包含共享信息 2：共享方 3：被共享方 [默认为0] |      |
| dateOrderedStartDate | String(10) | Y    | yyyy-MM-dd 出库单提交时间                                    |      |
| dateOrderedEndDate   | String(10) | Y    | yyyy-MM-dd 出库单提交时间                                    |      |
| status               | String()   | N    | 订单状态编码，详见[出库单状态列表](http://developer.winit.com.cn/document/detail/id/275.html) “status”不填写的时候，默认不包含VO（已作废）的订单，如需查询“已作废”的订单，请入参status="VO” |      |

#### 查询派送方式

| 名称        | 类型       | 必填 | 说明                                                         | 示例 |
| :---------- | :--------- | :--- | :----------------------------------------------------------- | :--- |
| warehouseID | String(10) | Y    | 海外仓ID 由万邑通定义的仓库ID,每个仓库有唯一一个对应的ID。 通过接口[queryWarehouse](http://developer.winit.com.cn/document/detail/id/43.html)得到出参：warehouseID |      |

#### 查询派送费用

| 名称                 | 类型     | 必填 | 说明                                              | 示例       |
| :------------------- | :------- | :--- | :------------------------------------------------ | :--------- |
| businessDocumentNo   | String() | N    | 海外仓出库单号,在用户创建海外仓出库单后获得，唯一 | WO04875043 |
| sellerNo             | String() | N    | 卖家订单号                                        |            |
| trackingNo           | String() | N    | 跟踪号/快递单号                                   |            |
| destinationWarehouse | String() | N    | 出库海外仓编码                                    | US0001     |
| orderDateFrom        | String() | N    | 下单起始日期(精确至日)                            | 2019-08-01 |
| orderDateTo          | String() | N    | 下单截止日期(精确至日)                            | 2019-08-26 |

#### 查询出库单

| 名称             | 类型     | 必填 | 说明                                             | 示例         |
| :--------------- | :------- | :--- | :----------------------------------------------- | :----------- |
| outboundOrderNum | String() | Y    | 海外仓出库单号在用户创建海外仓出库单后获得，唯一 | WO0000003291 |

#### 查询出库单

| 名称        | 类型     | 必填 | 说明                                                         | 示例                    |
| :---------- | :------- | :--- | :----------------------------------------------------------- | :---------------------- |
| trackingnos | String() | Y    | 跟踪号 支持winit订单号和跟踪号， 支持一次查询多个跟踪号 多个跟踪号用半角逗号分隔 最多不超过30个 | 05000196055,05000196086 |
| language    | String() | N    | 支持三种语言： 1.zh_CN:简体中文 2.zh_TW:繁体中文 3.en_US:英文 目前仅支持Winit物流轨迹的多语言，物流商返回的轨迹为原始轨迹，暂不支持多语言 | zh_CN                   |

#### 查询轨迹（库内）

| 名称        | 类型        | 必填 | 说明                                       | 示例         |
| :---------- | :---------- | :--- | :----------------------------------------- | :----------- |
| warehouseID | String()    | Y    | 出库海外仓ID                               | 1000069      |
| outboundNum | String(10)  | Y    | 海外仓出库单单号                           | WO0000001285 |
| trackingNum | String(100) | N    | 下出库单时选用的派送方式对应生成的快递单号 |              |

### 退货

#### 查询退货商品

| 名称     | 类型     | 必填 | 说明         | 示例 |
| :------- | :------- | :--- | :----------- | :--- |
| skuCode  | String() | N    | 商品编码     |      |
| cnName   | String() | N    | 商品中文名称 |      |
| name     | String() | N    | 商品英文名称 |      |
| isActive | String() | N    | 商品是否有效 |      |

#### 查询退货订单

| 名称                 | 类型       | 必填 | 说明                                                         | 示例               |
| :------------------- | :--------- | :--- | :----------------------------------------------------------- | :----------------- |
| returnGoodsOrderNo   | String(32) | N    | WINIT订单号-退货                                             | RT16000013812852CN |
| expressNo            | String(32) | N    | 退货运单号 仓库收到退货包裹扫描的运单号 （1）RMA退货：卖家填写的客户退货运单号 （2）无RMA退货：买家退货包裹的退货运单号 （3）派送失败：原出库单的运单号/某些供应商（DPD）的更换的退货运单号 |                    |
| outboundOrderNo      | String(32) | N    | 出库订单号                                                   |                    |
| rmaNo                | String(32) | N    | RMA                                                          |                    |
| customerOrderNo      | String(32) | N    | 客户订单号                                                   |                    |
| destroyOutboundOrder | String(32) | N    | 销毁出库单号                                                 |                    |
| originCode           | String(32) | N    | 创建分类 NR-仓库创建 OR-出库单启动退货                       |                    |
| warehouseCode        | String()   | N    | 退货仓库                                                     |                    |
| OderStartDatetime    | Date(10)   | Y    | 退货订单创建时间(From)                                       | 2018-06-8          |
| OderEndDatetime      | Date(10)   | Y    | 退货订单创建时间(To)                                         | 2018-06-8          |

## 全球直发API（ISP）

#### 查询轨迹

| 名称        | 类型     | 必填 | 说明                                                | 示例                                     |
| :---------- | :------- | :--- | :-------------------------------------------------- | :--------------------------------------- |
| trackingNOs | String() | Y    | 跟踪号/winit订单号 支持多个，逗号隔开               | 0B044518500034109567A,ID18956371887756CN |
| language    | String() | N    | 语言 1.zh_CN:简体中文 2.zh_TW:繁体中文 3.en_US:英文 | en_US                                    |

#### 查询物流费用

| 名称    | 类型       | 必填 | 说明       | 示例 |
| :------ | :--------- | :--- | :--------- | :--- |
| orderNo | String(60) | Y    | ISP 订单号 |      |

#### 查询订单详情

| 名称    | 类型       | 必填 | 说明        | 示例 |
| :------ | :--------- | :--- | :---------- | :--- |
| orderNo | String(60) | Y    | winit订单号 |      |

#### 查询提货地址

| 名称             | 类型       | 必填 | 说明                                                         | 示例 |
| :--------------- | :--------- | :--- | :----------------------------------------------------------- | :--- |
| winitProductCode | String(50) | Y    | 产品Code                                                     |      |
| dispatchType     | String(1)  | Y    | 发货方式 P:Winit揽收 S:自发快递 T:卖家自送 C:中邮揽收 D:DHL揽收 |      |

#### 查询小包物流产品/渠道

| 名称               | 类型       | 必填 | 说明               | 示例 |
| :----------------- | :--------- | :--- | :----------------- | :--- |
| warehouseID        | Long       | N    | 仓库ID             |      |
| productCatalogName | String(20) | N    | 产品类型,默认是ISP |      |

#### 查询国内验货仓

| 名称               | 类型       | 必填 | 说明             | 示例 |
| :----------------- | :--------- | :--- | :--------------- | :--- |
| productCode        | String(50) | Y    | 物流方式代码     |      |
| productCatalogName | String(20) | N    | 产品分类 默认ISP |      |

## 尾程联盟（LMA）

#### 获取面单

| 名称         | 类型       | 必填 | 说明         | 示例 |
| :----------- | :--------- | :--- | :----------- | :--- |
| winitOrderNo | String(60) | Y    | winit 订单号 |      |

#### 批量获取LMA运单号

| 名称          | 类型  | 必填 | 说明         | 示例              |
| :------------ | :---- | :--- | :----------- | :---------------- |
| winitOrderNos | Array | Y    | winit 订单号 | LMA010000001124CN |

## 查询费用

#### 查询费用-新

| 名称                 | 类型     | 必填 | 说明                                                         | 示例       |
| -------------------- | -------- | ---- | ------------------------------------------------------------ | ---------- |
| businessDocumentType | String() | N    | 业务分类 ISP:ISP:订单费； EC_ISP:其它费用(ISP/小包）； OC:海外仓出库费用； EC:海外仓其它费用（包含LMA）； GTC:国际送仓费； FLC:入库费用； SC:仓储费； RHC:退货费用； VAS:增值服务费。 |            |
| businessDocumentNo   | String() | O    | 业务订单号 国际送仓单的WINIT订单号 海外仓出库单的WINIT订单号 海外仓入单的WINIT订单号 ISP小包中国出库WINIT订单号 businessDocumentNo 和（deducationTimeStart+deducationTimeEnd）二选一必填 |            |
| deducationTimeStart  | String() | O    | 扣费开始日期 YYYY-MM-DD， 精确至日， 时间跨度不超过31天。 businessDocumentNo 和（deducationTimeStart+deducationTimeEnd）二选一必填 | 2020-09-01 |
| deducationTimeEnd    | String() | O    | 扣费截止日期 YYYY-MM-DD， 精确至日， 时间跨度不超过31天。 businessDocumentNo 和（deducationTimeStart+deducationTimeEnd）二选一必填 | 2020-10-01 |

#### 查询单据费用

| 名称                 | 类型     | 必填 | 说明                                                         | 示例       |
| :------------------- | :------- | :--- | :----------------------------------------------------------- | :--------- |
| businessDocumentType | String() | Y    | 业务分类 ISP:ISP订单费 EC_ISP:其它费用(ISP/小包） OC:海外仓出库费用 EC:海外仓其它费用 GTC:国际送仓费 FLC:入库费用 SC:仓储费 RHC:退货费用 VAS:增值服务费 | OC         |
| businessDocumentNo   | String() | N    | 业务订单号 国际送仓单的WINIT订单号 海外仓出库单的WINIT订单号 海外仓入库单的WINIT订单号 ISP小包中国出库WINIT订单号 |            |
| tradeDateFrom        | String() | Y    | 扣费开始日期 YYYY-MM-DD 精确至日 时间跨度不超过31天          | 2018-04-15 |
| tradeDateTo          | String() | Y    | 扣费截止日期 YYYY-MM-DD 精确至日 时间跨度不超过31天          | 2018-05-15 |