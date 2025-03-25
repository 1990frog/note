


conda create --name python310 python=3.10

pacman -S librdkafka extra/cyrus-sasl-gssapi extra/cyrus-sasl

conda active python310

vim .zshrc
export LIBRARY_PATH=/usr/local/lib:$LIBRARY_PATH  
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH  

conda install -c conda-forge openssl=3.2.0

pip install --no-binary confluent-kafka