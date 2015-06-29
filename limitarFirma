<?php 


if(!defined("IN_MYBB"))
{
    die("Direct initialization of this file is not allowed.<br /><br />Please make sure IN_MYBB is defined.");
}

// Información del plugin

function limitarFirma_info ()
{
    return array(
        "name"            => "limitarFirma",
        "description"    => "Establece unos mínimos de peso y tamaño para la firma",
        "website"        => "limitarFirma",
        "author"        => "Jase",
        "authorsite"    => "limitarFirma",
        "version"        => "0.1",
        "guid"             => "limitarFirma",
        "compatibility" => "*"
    );
}

$plugins->add_hook('usercp_start', 'signsize');
function signsize() {
	
    global $mybb, $error;

    preg_match_all("/\[img(.*?)\](.*?)\[\/img\]/i", $mybb->input['signature'], $matches, PREG_SET_ORDER);

    $kbsizetot = 0;
    
    foreach ($matches as $img) {
    $kbsize = strlen(@file_get_contents($img[2]));
    $kbsizetot += $kbsize;

    }
    
    if (($kbsizetot > 350000) && ($mybb->input['action'] == "do_editsig")) {

    $error = inline_error("La imagen pesa más de 350kb. Por favor, reduce su tamaño.");

    }  

   foreach ($matches as $img) {
    	$tamaño = getimagesize($img[2]);
    	$anchura = $tamaño[0];
    	$altura = $tamaño[1];

    }

    if (($anchura > 501 || $altura > 151) && ($mybb->input['action'] == "do_editsig"))  {
    	$error = inline_error("El tamaño de la imagen no es el adecuado.\nAnchura máxima 500px y altura máxima 150px");
    }
}

?>
