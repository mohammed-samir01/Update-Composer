# Update-Composer

# Navigate to your home directory
cd ~

# Download the Composer installer
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

# (Optional) Verify the installer
HASH="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

# Create a bin directory in your home directory if it doesn't exist
mkdir -p $HOME/bin

# Run the installer
php composer-setup.php --install-dir=$HOME/bin --filename=composer

# Remove the installer script
php -r "unlink('composer-setup.php');"

# Add the bin directory to your PATH
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc  # or source ~/.zshrc if you are using Zsh

# Verify the installation
composer --version
