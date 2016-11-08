# Magento 2 Snippets

## Log into separate file

```php
  
  public function logWrite($logType, $logMsg,$filename) {
        $writer = new \Zend\Log\Writer\Stream(BP . '/var/log/'.$filename);
        $logger = new \Zend\Log\Logger();
        $logger->addWriter($writer);

        switch (strtolower($logType)) {
            case 'alert':
                $logger->alert($logMsg);
                break;
            case 'notice':
                $logger->notice($logMsg);
                break;
            case 'info':
                $logger->info($logMsg);
                break;
            case 'debug':
                $logger->debug($logMsg);
                break;
            default:
                $logger->info("The log type is not exist");
                break;
        }
        return true;
    }

```
## Write a content to a file

```php
        $filesystem = $this->_objectManager->get('Magento\Framework\Filesystem');
				$writer = $filesystem->getDirectoryWrite(\Magento\Framework\App\Filesystem\DirectoryList::PUB);			
        /** @var \Magento\Framework\Filesystem\File\WriteInterface|\Magento\Framework\Filesystem\File\Write $file */
        $file = $writer->openFile('file.txt', 'w+');

        try {
            $file->lock();
            try {
                $file->write($content);
            } finally {
                $file->unlock();
            }
        } finally {
            $file->close();
        }
```
