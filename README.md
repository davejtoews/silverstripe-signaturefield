# silverstripe-signaturefield

_Forked from [micschk/silverstripe-signaturefield](https://github.com/micschk/silverstripe-signaturefield) which no longer appears to be maintained._

A silverstripe signature form field based on https://github.com/szimek/signature_pad

![screenshot](images/signaturefield.png)

### Usage

A signaturefield will be scaffolded if field is set to 'Signature' (field holds base64 png image of signature)

```php
use DaveJToews\SignatureField\Signature;

class Contract extends DataObject {

	private static $db = array(
		'Signature' => Signature::class,
	);

}
```

Or explicitly add a SignatureField to a form (eg for non-scafolded formfields or front-end)

```php
use DaveJToews\SignatureField\SignatureField;

...

	public function getCMSFields() {
		$fields = parent::getCMSFields();

		$fields->addFieldToTab('Root.Main',
				SignatureField::create('Signature')
			);

		return $fields;
	}
```

## Known Issues

Scaling issues may occur on high DPI screens: https://github.com/szimek/signature_pad/issues/679

## Development

The js is bundled using parcel.js. To make javascript changes

1. run `yarn install` to install dependencies.
2. make requisite changes in `javascript/src/signature_pad.init.js`
3. run `yarn build` to compile changes
