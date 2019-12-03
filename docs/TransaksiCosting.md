## Permintaan Costing Marketing

##### 1. Render List Permintaan Costing
**SSFile**: CostingMarketing.ss
![](../../../Pictures/Screenshot_2019-11-05_16-41-32.png)

```php
function index()
{
	$permission = $this->permission_check['reqcosting'];
	return $this
	->customise([
		'akses' => $permission,
		'url' => 'searchcosting',
		'Columns' => new ArrayList($this->getCustomColumns('costing'))
	])
	->renderWith(['CostingMarketing', 'Page']);
}
```
**Note:**
 >* **permission**: digunakan untuk mengambil hak akses untuk user yg login sekarang ini untuk menu permintan costing
* **url**: digunakan untuk menyimpan url api untuk mendapatkan data list Datatable list permintaan costing
* **Columns**: digunakan untuk menyimpan nama kolom table untuk list Datatable list permintaan costing


##### 2. View detail Permintaan Costing
**SSFile**: CostingMarketingViewPage.ss

```php
function viewreqcost()
{
	$permission = $this->permission_check['reqcosting'];

  	$id = $this->request->param("ID");
    $obj = CostingModel::getOneReqCost($id);
 
    if (isset($_REQUEST['print'])) {
      	return $this->customise(array(
        	'Data' => $obj
      	))->renderWith('CostingMarketingPrintPage');
    }else{
	    return $this->customise(array(
		  'Data' => $obj,
		  'akses' => $permission,
		  // 'edit_btn' => $allow_edit  
        ))->renderWith(array('CostingMarketingViewPage', 'Page'));
	}
}
```
**Note:**
> * **id**: digunakan untuk mendapatkan id permintaan costing dari list permintaan costing
* **obj**: digunakan untuk mendapatkan detail data dari permintaan costing 

##### 3. Edit/Add Permintaan Costing
**SSFile**: CostingMarketingForm.ss

```php
/**
 * Render add page for Costing Marketing Request
 */
function add()
{
	return $this
	->customise(['status' => 'Baru'])
	->renderWith(['CostingMarketingForm', 'Page']);
}
/**
 * Render edit page for Costing Marketing Request
 */
function editreqcost()
{
	$id = $this->request->param('ID');
	if (isset($id)){
	    $obj = CostingModel::getOneReqCost($id);

	    return $this
	    ->customise([
	      'status' => 'Edit',
	      'count' => sizeof($obj['Details']),
          'Data' => $obj
        ])
        ->renderWith(['CostingMarketingForm', 'Page']);
	}
}
```
**Note:**
> * **status**: digunakan untuk membedakan form untuk proses edit / new data
* **Data**: digunakan untuk mendapatkan detail data dari permintaan costing
* **count**: variable yang berisi jumlah data detail dari sebuah permintaan costing

```php
/**
 * [cekhargacosting description]
 * Get harga costing from harga input awal
 * @param  [type] $harga [description]
 * @return [type]        [description]
 */
public function cekhargacosting()
{
	$size = (isset($_REQUEST['size'])) ? $_REQUEST['size'] : '';
	$kdjenisrm = (isset($_REQUEST['kdjenisrm'])) ? $_REQUEST['kdjenisrm'] : '';
	$harga = (isset($_REQUEST['harga'])) ? $_REQUEST['harga'] : '';
	$cekharga = CostingModel::cekHargaCosting($kdjenisrm, $size, $harga);
	
	return json_encode([
		'data' => $cekharga['listData'],
		'sql' => $cekharga['sql']
	]);
}
```

**Note:**
> * **size**: digunakan untuk mengambil parameter dari size product terpilih
* **kdjenisrm**: digunakan untuk mengambil parameter dari kode jenis rm product terpilih
* **harga**: variable yang berisi harga patokan yang diinputkan di permintaan costing

**Rule:**
> * satuan default setelah memilih product adalah 'MC' dan jika dalam product yang terpilih tidak ada satuan 'MC' maka yang digunakan adalah satuan terbesar dari product tersebut. 
* untuk menentukan harga size patokan dan harga size costing didapatkan dengan parameter 'kdjenisrm' dan 'size' dari product terpilih. Dan sebagai patokan untuk menentukan harganya ada master harga rm yg berisikan range bawah dan atas untuk menentukan harga. 
* Untuk cek harga costing mengunakan stored procedure yang sudah dibuat di SQL Server (CekHargaCoasting)

