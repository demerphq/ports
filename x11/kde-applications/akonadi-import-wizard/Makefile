COMMENT =	PIM Akonadi import wizard
DISTNAME =	akonadi-import-wizard-${VERSION}
CATEGORIES =	devel

SHARED_LIBS +=  KPimImportWizard       1.1 # 5.13.2

WANTLIB += ${COMPILER_LIBCXX} Grantlee_Templates KF5AkonadiContact
WANTLIB += KF5AkonadiCore KF5AkonadiMime KF5AkonadiWidgets KF5Archive
WANTLIB += KF5Auth KF5AuthCore KF5Codecs KF5Completion KF5ConfigCore
WANTLIB += KF5ConfigGui KF5ConfigWidgets KF5Contacts KF5CoreAddons
WANTLIB += KF5Crash KF5DBusAddons KF5GrantleeTheme KF5I18n KF5IMAP
WANTLIB += KF5IdentityManagement KF5IdentityManagementWidgets
WANTLIB += KF5ItemModels KF5KIOCore KF5Libkdepim KF5Libkleo KF5MailCommon
WANTLIB += KF5MailImporter KF5MailImporterAkonadi KF5MailTransport
WANTLIB += KF5MessageComposer KF5MessageCore KF5MessageViewer
WANTLIB += KF5Mime KF5MimeTreeParser KF5PimCommon KF5PimCommonAkonadi
WANTLIB += KF5PimCommonAutoCorrection KF5PimTextEdit KF5Service
WANTLIB += KF5Wallet KF5WidgetsAddons KF5XmlGui Qt5Concurrent
WANTLIB += Qt5Core Qt5DBus Qt5Gui Qt5Network Qt5Widgets Qt5Xml
WANTLIB += assuan c gpgme gpgmepp m qgpgme qt5keychain

#WANTLIB += lib/inotify/inotify

MODKDE5_TRANSLATIONS = yes
MODKDE5_ICON_CACHE = yes
MODKDE5_DESKTOP_FILE = yes

MODKF5_L10N_CONFLICT = yes
MODKF5_I18N_CONFLICT = yes

BUILD_DEPENDS =	devel/boost

LIB_DEPENDS =	devel/kf5/karchive \
		devel/kf5/kauth \
		devel/kf5/kcodecs \
		devel/kf5/kcompletion \
		devel/kf5/kconfig \
		devel/kf5/kconfigwidgets \
		devel/kf5/kcontacts \
		devel/kf5/kcoreaddons \
		devel/kf5/ki18n \
		devel/kf5/kitemmodels \
		devel/kf5/kservice \
		devel/kf5/kwidgetsaddons \
		devel/kf5/kxmlgui \
		security/gpgme,-qt \
		devel/libinotify \
		x11/kde-applications/akonadi \
		x11/kde-applications/kidentitymanagement \
		x11/kde-applications/kimap \
		x11/kde-applications/kmime \
		x11/kde-applications/kpimtextedit \
		x11/kde-applications/libkdepim \
		x11/kde-applications/libkleo \
		x11/kde-applications/mailimporter \
		x11/kde-applications/messagelib \
		x11/kde-applications/pimcommon \
		x11/kde-applications/mailcommon

CXXFLAGS +=	-I${LOCALBASE}/include/KF5/MessageViewer

.include <bsd.port.mk>
