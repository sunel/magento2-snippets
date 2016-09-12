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
