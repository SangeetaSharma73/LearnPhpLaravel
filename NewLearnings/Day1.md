# How to make DOMPDF

1. Install Dompdf Package

`composer require barryvdh/laravel-dompdf`

2. Service Provider and Alias (Laravel 5.5 and up)

- Add the service provider to the config/app.php file:

'providers' => [
    Barryvdh\DomPDF\ServiceProvider::class,
],

- Then, add the alias to the config/app.php file:

'aliases' => [
    'PDF' => Barryvdh\DomPDF\Facade::class,
],

3. Publish the Configuration (Optional)

`php artisan vendor:publish --provider="Barryvdh\DomPDF\ServiceProvider"`

- This will create a config/dompdf.php file where you can modify settings like paper size, fonts, and other options.


4. Create a PDF View

- Next, create a view that you want to convert into a PDF. In your resources/views/ directory, create a new Blade file, e.g., invoice.blade.php.

<!DOCTYPE html>
<html>
<head>
    <title>Invoice</title>
</head>
<body>
    <h1>Invoice #{{ $invoice->id }}</h1>
    <p>Date: {{ $invoice->date }}</p>
    <p>Total: {{ $invoice->total }}</p>
</body>
</html>


5. Generate PDF in Controller
- In your controller, you can now use Dompdf to generate the PDF from the view.

use PDF; // Make sure to include the alias at the top of the controller

class InvoiceController extends Controller
{
    public function downloadInvoice($invoiceId)
    {
        // Fetch the invoice data from the database
        $invoice = Invoice::find($invoiceId);

        // Load the view and pass the data
        $pdf = PDF::loadView('invoice', compact('invoice'));

        // Return the generated PDF as a download
        return $pdf->download('invoice_' . $invoice->id . '.pdf');
    }
}


6. Route - Define a route that triggers the PDF generation. Add the following route in your routes/web.php file:

Route::get('invoice/{id}/download', [InvoiceController::class, 'downloadInvoice']);

7. Test the PDF Generation
- Now, you can navigate to the route in your browser to generate and download the PDF:

http://yourapp.test/invoice/1/download


8. Optional: Stream the PDF (View in Browser)

- If you want to display the PDF in the browser instead of downloading it, you can use the stream method instead of download:

return $pdf->stream('invoice_' . $invoice->id . '.pdf');


9. Advanced Customization:
- Paper Size & Orientation: You can specify the paper size and orientation directly when generating the PDF:

` $pdf = PDF::loadView('invoice', compact('invoice'))->setPaper('a4', 'landscape');`

- CSS and Fonts: You can style the PDF using inline styles or link to external stylesheets. Dompdf supports basic HTML and CSS, but it might not fully support advanced CSS like Flexbox.


# How i have made

1. Verify Installation
- Make sure the package is installed by running the following command:

`composer show barryvdh/laravel-dompdf`

2. Test PDF Generation
- You can now go ahead and implement the PDF generation in your controller (as described earlier). For example, try generating a simple PDF and check if everything works fine.

use PDF;

class TestController extends Controller
{
    public function generatePDF()
    {
        $pdf = PDF::loadView('pdf.test'); // Replace with your view
        return $pdf->download('test.pdf'); // Test PDF generation
    }
}


- Create a simple view like resources/views/pdf/test.blade.php:

<!DOCTYPE html>
<html>
<head>
    <title>Test PDF</title>
</head>
<body>
    <h1>Hello, this is a test PDF!</h1>
</body>
</html>

- And add a route in routes/web.php:

`Route::get('test-pdf', [TestController::class, 'generatePDF']);`
