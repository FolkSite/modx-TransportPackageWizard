#Modx Transport Package Wizard#
###An easier way to create Transport Packages for Modx 2.2+###
--------------------------------------------------------------
An ongoing project to create an easy-to-use library for transport package creation in modx.
Very basic at this point, usage is outlined below

```ruby
/** Initialise the Wizard class */
$Package = new TransportPackageWizard(array(
  				DEFINE => array(
							'MODX_CORE_PATH' => dirname(dirname(__FILE__)).'/core/',
							'PKG_NAME' => 'My Package Name',
							'PKG_NAME_LOWER' => 'mypackagename',
							'PKG_VERSION' => '1.0',
							'PKG_RELEASE' => 'beta1'
						)
				));

/** Add files & directories to package */
$Package->addDirectory('path/to/directory', "{assets_path}components/mypackagename/");

/** Create a Category element */
$myCategory = $Package->addCategory('My Category Name'); 

/** Add Elements to the category */
$myCategory->addSnippet('Snippet-Name');
$myCategory->addChunk('Chunk-Name');
$myCategory->addTemplate('Template-Name',true);
$myCategory->addTV('TV-Name');

/** Set a modx System Setting after install */
$Package->PostInstall->setOption('key','value','xtype','area','namespace');

/** Build the transport package for deployment */
$Package->build();

```
