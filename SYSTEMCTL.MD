============ JOURNALCTL ==============================

https://habr.com/ru/companies/ruvds/articles/533918/

journalctl -u mediamtx.service

============= SYSTEMCTL ==============================

https://losst.pro/upravlenie-sluzhbami-linux#toc-6-perezapusk-sluzhby

sudo systemctl daemon-reload
sudo systemctl start mediamtx.service

AUTOSTART
sudo systemctl enable mediamtx.service

============ EXAMPLE ================================

[Unit]
Description=set mediamtx

[Service]
Type=oneshot
User=ihor
StandardOutput=journal
StandardError=journal

WorkingDirectory=/home/ihor/mediamtx
ExecStartPre=/bin/sleep 30
ExecStart=/bin/bash -c '/home/ihor/mediamtx/mediamtx'
Restart=on-failure

[Install]
WantedBy=multi-user.target


=====================================================