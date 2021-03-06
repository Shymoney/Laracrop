# Laracrop
Simple crop image Laravel with jCrop

![alt crop](https://github.com/Aris-haryanto/Laracrop/blob/master/crop.png)

### How to install
- Run in your terminal:
```
$ cd yourprojectdirectory
$ composer require arisharyanto/laracrop
```
- Add the service providers in config/app.php:
```
Arisharyanto\Laracrop\LaracropServiceProvider::class,
```
- Run this command in the terminal
```
$ php artisan vendor:publish --provider="Arisharyanto\Laracrop\LaracropServiceProvider"  
```
- Setup the default config in `config/laracrop.php` 
```
# IMPORTANT! the config which is mark with double asterisk (**) you must change this to something unique after install laracrop because security risk

    'route_prefix' => "laracrop",         # **route prefix to ajax url
    'upload_url' => "upload/image",       # **route url to ajax upload url route_prefix/upload_url
    'path_upload' => "public/filetmp",    # **where you put file upload
    'image_url' => "filetmp",             # **please note you must change this with same url from path_upload exclude "public"

    'aspectratio' => "1",                 # 1 to set ratio same with width and height of image or 
                                          # you can set with custom ratio like 3/1 or 2/1 whatever you want
                                          # set 0 to free crop
                                          
    'minsize' => "[200, 200]",            # Minimum selection size [ width, height ] set 0 to remove min size
    'maxsize' => "[500, 500]",            # Maxium selection size [ width, height ] set 0 to remove max size
    'bgcolor' => "black",                 # Color value for background shading
    'bgopacity' => "0.6"                  # Opacity value for background shading
    'boxwidth' => "600",                  # set image width 
    'boxheight' => "600"                  # set image heigth
```

### How to use

In your blade view
```
# adding laracrop css set true to embed bootstrap css or set empty the parameters to not embeded
@laracropCss(true)

  # you can add custom setting for some croping 
  @laracrop(name=desktop | aspectratio=1 | minsize=[300, 300] | bgcolor=black | bgopacity=0.7) 
  
  # or you just write with name parameters like this to set default config
  @laracrop(mobile)
  
  # NOTE: name is required

# adding laracrop JS set true to embed jQuery or set empty the parameters to not embeded
@laracropJs(true)
```

add `use Arisharyanto\Laracrop\Laracrop` in your Controller

and add this inside your function
```
  # call this function with parameter $request->input('mobile') from view @laracrop(mobile) will return filename to store in database
  $getName = Laracrop::cropImage($request->input('desktop'));
  
  #call this function at the end of your function to clean temporary file when your uploading image to crop 
  Laracrop::cleanCropTemp();
```

### Credits
- [https://github.com/tapmodo/Jcrop/](https://github.com/tapmodo/Jcrop/)

### License

See the license [https://github.com/Aris-haryanto/Laracrop/blob/master/LICENSE](https://github.com/Aris-haryanto/Laracrop/blob/master/LICENSE)


### Author

Aris Haryanto
visit my website [https://arindasoft.wordpress.com/](https://arindasoft.wordpress.com/)
