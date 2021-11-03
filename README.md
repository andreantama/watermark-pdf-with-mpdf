# Add a watermark to an existing pdf file using laravel 8 and mpdf


## Install Step 1

 ```bash
 composer require mpdf/mpdf
 ```
 
 

## Install Step 2

```PHP
/* https://mpdf.github.io/installation-setup/installation-v7-x.html */
use Illuminate\Http\File;
use Illuminate\Support\Facades\Storage;


public function DicabutWatermarkDokumenHandle()
    {
        //C:\xampp\htdocs\simregs\storage\app\file.jpg
        // Source file and watermark config 
        $file = Storage::path('RegulasiDokumenDicabut\Regulasi_Dicabut_1E_2021_11_03_02_52_18_.pdf'); 
        $text_image = Storage::path('RegulasiDokumenDicabut\simregs.png');
        
        $mpdf = new \Mpdf\Mpdf();
        
        $pagecount = $mpdf->SetSourceFile($file);
        $tplId = $mpdf->ImportPage($pagecount);
        $mpdf->UseTemplate($tplId);

        $mpdf->SetWatermarkImage($text_image);
        $mpdf->showWatermarkImage = true;

        //$mpdf->WriteHTML('You can use this just like normal, but also import and use templates...');
        //$mpdf->Output();
        $mpdf->Output($file, \Mpdf\Output\Destination::FILE);
    }
```
