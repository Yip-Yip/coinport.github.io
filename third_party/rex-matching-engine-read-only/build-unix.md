UNIX BUILD NOTES
====================
Build on Ubuntu 12.04, Linux kernel 3.2.0-23-generic, GCC 4.6.3

Dependencies
---------------------
For basic compilation tools:

	sudo apt-get install build-essential
For quickfix lib (e.g. quickfix/FileStore.h):

	sudo apt-get install libquickfix-dev
For log4 lib (e.g. log4cxx/logger.h):

	sudo apt-get install liblog4cxx10-dev
For ace lib, (e.g. ace/Task.h):

	sudo apt-get install libace-dev

Build and run copied version
---------------------

Build
---------------------
	svn checkout http://pugixml.googlecode.com/svn/tags/latest/ pugixml
	svn checkout http://rex-matching-engine.googlecode.com/svn/trunk/ rex-matching-engine-read-only
    cd rex-matching-engine-read-only/src/
    ln -sf ../../../pugixml/src/ rex/pugixml
Create Makefile with following content:

    all:
        g++ Main.cpp rex/*.cpp rex/*.h rex/pugixml/pugixml.cpp -lquickfix -llog4cxx -lACE -g3 -o rex-matching-engine
Then

    make

Run
---------------------
Modify config file:

    sed -i 's#/Users/ben/dev/orca/rex/Debug/config/FIX42.xml#./config/FIX42.xml#g' config/fix.ini
Run:

    ./rex-matching-engine
    display
    quit
Here is output from console:

    INFO [0x7faf17348780] (rex/Exchange.cpp:55) - Starting Rex
    INFO [0x7faf17348780] (rex/Exchange.cpp:56) - Using REX_HOME /mnt/ssd/coinport/coinport/src/third_party/rex-matching-engine-read-only/src
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:30) - Initializing Order Book Manager
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for IBM
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for MSFT
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for AAPL
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for C
    INFO [0x7faf0f735700] (rex/OrderBook.cpp:177) - OrderBook thread now running for MSFT
    INFO [0x7faf0ff36700] (rex/OrderBook.cpp:177) - OrderBook thread now running for IBM
    INFO [0x7faefffff700] (rex/OrderBook.cpp:177) - OrderBook thread now running for AAPL
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for GOOG
    INFO [0x7faf0ef34700] (rex/OrderBook.cpp:177) - OrderBook thread now running for C
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for T
    INFO [0x7faf0e733700] (rex/OrderBook.cpp:177) - OrderBook thread now running for GOOG
    INFO [0x7faf0df32700] (rex/OrderBook.cpp:177) - OrderBook thread now running for T
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for JPM
    INFO [0x7faf17348780] (rex/OrderBookManager.cpp:32) - Creating order book for GS
    INFO [0x7faf17348780] (rex/FixEngine.cpp:46) - Starting Fix Engine
    INFO [0x7faf0d731700] (rex/OrderBook.cpp:177) - OrderBook thread now running for JPM
    INFO [0x7faf0cf30700] (rex/OrderBook.cpp:177) - OrderBook thread now running for GS
    <20140107-15:50:41.123, FIX.4.2:REX->CLIENT1, event>
    (Created session)
    <20140107-15:50:41.124, FIX.4.2:REX->CLIENT2, event>
    (Created session)
    <20140107-15:50:41.126, FIX.4.2:REX->CLIENT3, event>
    (Created session)
    <20140107-15:50:41.128, FIX.4.2:REX->CLIENT4, event>
    (Created session)
    <20140107-15:50:41.130, FIX.4.2:REX->CLIENT5, event>
    (Created session)
    display
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for AAPL
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for C
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for GOOG
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for GS
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for IBM
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for JPM
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for MSFT
    INFO [0x7faf17348780] (rex/OrderBook.cpp:164) - Displaying order book for T

    quit
    INFO [0x7faefffff700] (rex/OrderBook.cpp:191) - OrderBook thread exited for AAPL
    INFO [0x7faf0ef34700] (rex/OrderBook.cpp:191) - OrderBook thread exited for C
    INFO [0x7faf0e733700] (rex/OrderBook.cpp:191) - OrderBook thread exited for GOOG
    INFO [0x7faf0cf30700] (rex/OrderBook.cpp:191) - OrderBook thread exited for GS
    INFO [0x7faf0ff36700] (rex/OrderBook.cpp:191) - OrderBook thread exited for IBM
    INFO [0x7faf0d731700] (rex/OrderBook.cpp:191) - OrderBook thread exited for JPM
    INFO [0x7faf0f735700] (rex/OrderBook.cpp:191) - OrderBook thread exited for MSFT
    INFO [0x7faf0df32700] (rex/OrderBook.cpp:191) - OrderBook thread exited for T

