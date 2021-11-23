# tpm notes

tpm2 software projects and docs:
* https://tpm2-software.github.io/software/
* https://tpm2-software.github.io/tutorials/
* https://github.com/tpm2-software/tpm2-pkcs11
* https://github.com/tpm2-software/tpm2-pkcs11/blob/master/docs/EAP-TLS.md
* https://github.com/tpm2-software/tpm2-pkcs11/blob/master/docs/SSH.md
* https://github.com/tpm2-software/tpm2-abrmd
* https://github.com/tpm2-software/tpm2-tss
* https://github.com/tpm2-software/tpm2-tss-engine

tpm2 disk encryption tutorial with tpm, tss and tpm2-software info and short
rsa key pair example:
* https://tpm2-software.github.io/2020/04/13/Disk-Encryption.html
* https://www.intel.com/content/www/us/en/developer/articles/code-sample/protecting-secret-data-and-keys-using-intel-platform-trust-technology.html

wpa supplicant:
* https://superuser.com/questions/1510368/configuring-wpa-supplicant-to-use-tpm2-pkcs11-tools
* https://w1.fi/cgit/hostap/plain/wpa_supplicant/examples/openCryptoki.conf
* https://www.spinics.net/lists/hostap/msg04008.html

ubuntu, tpm simulator:
* https://francislampayan.medium.com/how-to-setup-tpm-simulator-in-ubuntu-20-04-25ec673b88dc

tpm2 device emulation with qemu:
* https://tpm2-software.github.io/2020/10/19/TPM2-Device-Emulation-With-QEMU.html
* https://www.smoothnet.org/qemu-tpm/
* https://qemu-project.gitlab.io/qemu/specs/tpm.html

software tpm2:
* https://github.com/stefanberger/swtpm
* https://github.com/stefanberger/swtpm/wiki
* https://launchpad.net/~stefanberger/+archive/ubuntu/swtpm-focal

ssh with tpm2-pkcs11 on debian and slackware/from source:
* https://donjon.ledger.com/ssh-with-tpm/
* https://incenp.org/notes/2020/tpm-based-ssh-key.html

ssh, gnupg, openvpn on archlinux:
* https://www.evolware.org/?p=597

tpm for private key protection discussion:
* https://ml01.01.org/hyperkitty/list/tpm2@lists.01.org/thread/3O4CQKKRXFTUDSHADTGRYWHFJFWJBLYA/
* https://superuser.com/questions/1508874/how-to-manage-rsa-keypair-in-tpm2-using-linux

tpm info, docs:
* https://wiki.archlinux.org/title/Trusted_Platform_Module
* https://www.cs.unh.edu/~it666/reading_list/Hardware/tpm_fundamentals.pdf
* https://www.thinkwiki.org/wiki/Embedded_Security_Subsystem
* https://www.lorier.net/docs/tpm
* https://lwn.net/Articles/674751/
* https://www.linuxplumbersconf.org/event/4/contributions/302/attachments/343/572/LPC2019.pdf

openconnect:
* https://www.infradead.org/openconnect/pkcs11.html
* http://lists.infradead.org/pipermail/openconnect-devel/2017-September/004511.html
* http://www.infradead.org/openconnect/tpm.html

pkcs11 info, uris:
* https://en.wikipedia.org/wiki/PKCS_11
* https://datatracker.ietf.org/doc/html/rfc7512

network manager, pkcs11 integration:
* https://wiki.gnome.org/Projects/NetworkManager/PKCS11
* https://bugzilla.gnome.org/show_bug.cgi?id=719982
* https://bugzilla.redhat.com/show_bug.cgi?id=1821924

p11-glue projects, including p11-kit, docs:
* https://p11-glue.github.io/p11-glue/
* https://p11-glue.github.io/p11-glue/p11-kit.html
* https://p11-glue.github.io/p11-glue/trust-module.html
* https://p11-glue.github.io/p11-glue/p11-kit/manual/

opencryptoki:
* https://github.com/opencryptoki/opencryptoki
* https://github.com/opencryptoki/opencryptoki/blob/master/doc/opencryptoki-howto.md
* https://github.com/opencryptoki/openssl-ibmpkcs11

strongSwan ipsec and tpm:
* https://wiki.strongswan.org/projects/strongswan/wiki/TPMPlugin

tpm2 talks:
* https://www.barbhack.fr/slides/2021/barbhack2021_tpm_auth.pdf
* https://www.sstic.org/media/SSTIC2021/SSTIC-actes/protecting_ssh_authentication_with_tpm_20/SSTIC2021-Slides-protecting_ssh_authentication_with_tpm_20-iooss.pdf
* https://archive.fosdem.org/2019/schedule/event/tpm2/attachments/slides/3111/export/events/attachments/tpm2/slides/3111/FOSDEM_TPM_TSS2_0.pdf

man tpm2_import:
* https://www.mankier.com/1/tpm2_import

p11tool/pkcs11-tool rsa key import issue, importing rsa keys should be
rejected:
* https://github.com/tpm2-software/tpm2-pkcs11/pull/698

tpm2-pkcs11 guide:
* https://azure.github.io/iot-identity-service/pkcs11/tpm2-pkcs11.html

safeboot:
* https://github.com/osresearch/safeboot
* https://safeboot.dev/

GSoC libsecret TPM2 support:
* https://gitlab.gnome.org/Teams/Engagement/gsoc-2021/-/issues/13
* https://dnuka.github.io/gsoc21-final-report.html
* https://gitlab.gnome.org/GNOME/libsecret
