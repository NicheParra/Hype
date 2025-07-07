import React, { useState, useEffect, useCallback } from 'react';
import { initializeApp } from 'firebase/app';
import { getAuth, signInAnonymously, onAuthStateChanged, signInWithCustomToken } from 'firebase/auth';
import { getFirestore, collection, doc, setDoc, onSnapshot, query, where } from 'firebase/firestore';
import { Video, MessageCircle, User, Wallet, Clock, TrendingUp, Upload, X, Trophy, Home, Users, Inbox, Link as LinkIcon, Edit, Globe, Lock, ChevronLeft, Radio, Camera, Search, Eye, Gift, Percent, Plus, Hash, Share2, Menu, QrCode, Shield, Heart, Bookmark, FileVideo, Bell, Music, Tv, Activity, Settings2, SlidersHorizontal, UserMinus, Megaphone, Download, Trash2, WifiOff, Flag, HelpCircle, Info, LogOut, RefreshCw, Copy, Send } from 'lucide-react';

// --- CONFIGURACIÓN DE FIREBASE ---
const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : { apiKey: "...", authDomain: "...", projectId: "...", storageBucket: "...", messagingSenderId: "...", appId: "..." };
const appId = typeof __app_id !== 'undefined' ? __app_id : 'hype-app-default';
const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : undefined;

// --- DATOS DE EJEMPLO (MOCK DATA) ---
const mockUser = { username: '@elcreador', profilePic: 'https://placehold.co/100x100/2563eb/ffffff?text=EC', bio: 'Creador de contenido en Hype. ¡Vota por mis videos! 🚀', link: 'beacons.ai/elcreador', following: 150, followers: 3200, votes: 28700, isPrivate: false, };
const mockVideos = [ { id: '1', user: '@elcreador', description: '¡Mi primer video en Hype! ¿Llegará al Top 3?', comments: 12, votes: 1520, likes: 22400, views: 17300, videoUrl: 'https://placehold.co/480x854/000000/ffffff?text=Video+1', globalRank: 8934 }, { id: '2', user: '@cocinaconarte', description: 'Receta rápida para una cena increíble 🍳', comments: 45, votes: 980, likes: 15000, views: 12100, videoUrl: 'https://placehold.co/480x854/111111/ffffff?text=Video+2', globalRank: 15234 }, { id: '3', user: '@fitlife', description: 'Rutina de ejercicios de 5 minutos', comments: 8, votes: 2300, likes: 31000, views: 25000, videoUrl: 'https://placehold.co/480x854/222222/ffffff?text=Video+3', globalRank: 3102 }, { id: '4', user: '@viajandoporelmundo', description: 'La vista más espectacular que he visto', comments: 23, votes: 540, likes: 11200, views: 8900, videoUrl: 'https://placehold.co/480x854/333333/ffffff?text=Video+4', globalRank: 29870 }, { id: '5', user: '@gamerpro', description: 'Jugada épica en el torneo', comments: 50, votes: 3100, likes: 55000, views: 42300, videoUrl: 'https://placehold.co/480x854/444444/ffffff?text=Video+5', globalRank: 1056 }, { id: '6', user: '@elcreador', description: 'Un día en la oficina', comments: 22, votes: 1800, likes: 21000, views: 19800, videoUrl: 'https://placehold.co/480x854/555555/ffffff?text=Video+6', globalRank: 6543 }, ];
const mockProfileTabs = { voted: mockVideos.slice(1, 4), shared: mockVideos.slice(3, 5), saved: mockVideos.slice(0, 2), drafts: [{ id: 'd1', videoUrl: 'https://placehold.co/480x854/666/fff?text=Borrador' }] };
const mockFriendsContent = { stories: [ { id: 's1', user: '@gamerpro', img: 'https://placehold.co/150x150/ff6347/ffffff?text=GP', seen: false }, { id: 's2', user: '@fitlife', img: 'https://placehold.co/150x150/32cd32/ffffff?text=FL', seen: false }, { id: 's3', user: '@viajandoporelmundo', img: 'https://placehold.co/150x150/1e90ff/ffffff?text=V', seen: true }, ], live: [ { id: 'l1', user: '@cocinaconarte', title: 'Cocinando pasta en vivo' }, ], videos: [ { id: 'fv1', user: '@gamerpro', description: 'Probando el nuevo mapa, solo para amigos!', videoUrl: 'https://placehold.co/480x854/6a0dad/ffffff?text=Amigos+1', comments: 5 }, { id: 'fv2', user: '@fitlife', description: 'Mi progreso en el gimnasio', videoUrl: 'https://placehold.co/480x854/006400/ffffff?text=Amigos+2', comments: 12 }, ] };
const mockRankings = { daily: [...mockVideos].sort((a,b) => b.votes - a.votes).slice(0, 3), weekly: [...mockVideos].sort((a,b) => (b.votes * 1.5) - (a.votes * 0.8)).sort((a,b) => b.votes - a.votes), monthly: [...mockVideos].sort((a,b) => b.comments - a.comments), };
const mockRewards = { redeem: [ { id: 'r1', title: 'Tarjeta Regalo Amazon', points: 5000, icon: 'https://placehold.co/100x100/ff9900/ffffff?text=A' }, { id: 'r2', title: 'Donación a UNICEF', points: 1000, icon: 'https://placehold.co/100x100/00aeef/ffffff?text=U' }, { id: 'r3', title: 'Merchandising Hype', points: 10000, icon: 'https://placehold.co/100x100/2563eb/ffffff?text=H' }, ], discounts: [ { id: 'd1', title: '20% en Tiendas de Ropa', partner: 'FashionApp', icon: 'https://placehold.co/100x100/db2777/ffffff?text=F' }, { id: 'd2', title: '10% en Videojuegos', partner: 'GameStore', icon: 'https://placehold.co/100x100/7c3aed/ffffff?text=G' }, ] };
const mockTrending = ["#verano2025", "#retocomida", "@hypecreadores", "#baileviral", "mejoresjugadas"];
const mockProfileViewers = [ { id: 'u1', username: '@gamerpro', profilePic: 'https://placehold.co/100x100/7c3aed/ffffff?text=GP' }, { id: 'u2', username: '@viajandoporelmundo', profilePic: 'https://placehold.co/100x100/1e90ff/ffffff?text=V' }, { id: 'u3', username: '@fitlife', profilePic: 'https://placehold.co/100x100/32cd32/ffffff?text=FL' }, ];
const mockRecommendedUsers = [ { id: 'u4', username: '@nuevotalento', bio: 'Empezando en Hype!' }, { id: 'u5', username: '@comediaen1min', bio: 'Risas garantizadas' }, ];
const mockHypeFriends = [ { id: 'f1', username: '@gamerpro', profilePic: 'https://placehold.co/100x100/7c3aed/ffffff?text=GP' }, { id: 'f2', username: '@fitlife', profilePic: 'https://placehold.co/100x100/32cd32/ffffff?text=FL' }, { id: 'f3', username: '@cocinaconarte', profilePic: 'https://placehold.co/100x100/ff8c00/ffffff?text=C' } ];

// --- COMPONENTES DE LA UI ---

const CountdownTimer = ({ isSmall = false }) => { const calculateTimeLeft = () => { const now = new Date(); const revealTime = new Date(); revealTime.setHours(21, 0, 0, 0); if (now > revealTime) revealTime.setDate(revealTime.getDate() + 1); const difference = revealTime - now; let timeLeft = {}; if (difference > 0) { timeLeft = { hours: Math.floor((difference / (1000 * 60 * 60)) % 24), minutes: Math.floor((difference / 1000 / 60) % 60), seconds: Math.floor((difference / 1000) % 60), }; } return timeLeft; }; const [timeLeft, setTimeLeft] = useState(calculateTimeLeft()); useEffect(() => { const timer = setTimeout(() => { setTimeLeft(calculateTimeLeft()); }, 1000); return () => clearTimeout(timer); }); if (isSmall) { return <Clock size={12} className="text-white"/> } return <div className="fixed top-4 right-4 bg-black bg-opacity-50 text-white p-2 rounded-lg backdrop-blur-sm z-20 flex items-center space-x-2 border border-gray-700"><Clock size={18} className="text-blue-400" /><span className="font-mono text-sm">{String(timeLeft.hours).padStart(2, '0')}:{String(timeLeft.minutes).padStart(2, '0')}:{String(timeLeft.seconds).padStart(2, '0')}</span></div>; };

const VideoPlayer = ({ video, onVote, canVote, isVoted, onLike, isLiked, onSave, isSaved, onShare, isRevealTimePassed, isFriendFeed = false }) => ( <div className="h-full w-full snap-start relative flex items-center justify-center bg-black"> <div className="absolute inset-0 bg-cover bg-center" style={{backgroundImage: `url(${video.videoUrl})`}}><div className="absolute inset-0 bg-black bg-opacity-20"></div></div> <div className="absolute bottom-24 left-0 p-4 text-white z-10 w-full"><p className="font-bold text-lg drop-shadow-lg">{video.user}</p><p className="text-sm drop-shadow-md">{video.description}</p></div> <div className="absolute bottom-24 right-2 flex flex-col items-center space-y-4 z-10"> {!isFriendFeed && (<button onClick={() => onVote(video.id)} disabled={!canVote || isVoted} className={`flex flex-col items-center transition-transform duration-200 ease-in-out ${canVote && !isVoted ? 'hover:scale-110' : ''} ${isVoted ? 'scale-110' : ''}`}><div className={`p-3 rounded-full transition-colors ${isVoted ? 'bg-blue-500' : 'bg-gray-800 bg-opacity-70'}`}><TrendingUp size={28} color={isVoted ? 'white' : '#60a5fa'}/></div><span className="text-xs font-bold mt-1 text-white">{isVoted ? '¡VOTADO!' : 'Votar'}</span></button>)} <button onClick={() => onLike(video.id)} className="flex flex-col items-center"><div className="p-3 bg-gray-800 bg-opacity-70 rounded-full"><Heart size={28} className={`transition-colors ${isLiked ? 'text-red-500 fill-current' : 'text-white'}`}/></div>{isRevealTimePassed && <span className="text-sm font-semibold mt-1 text-white">{video.likes.toLocaleString()}</span>}</button> <div className="flex flex-col items-center"><div className="p-3 bg-gray-800 bg-opacity-70 rounded-full"><MessageCircle size={28} color="white" /></div><span className="text-sm font-semibold mt-1 text-white">{video.comments}</span></div> <button onClick={() => onSave(video.id)} className="flex flex-col items-center"><div className="p-3 bg-gray-800 bg-opacity-70 rounded-full"><Bookmark size={28} className={`transition-colors ${isSaved ? 'text-yellow-400 fill-current' : 'text-white'}`}/></div></button> <button onClick={() => onShare(video)} className="flex flex-col items-center"><div className="p-3 bg-gray-800 bg-opacity-70 rounded-full"><Share2 size={28} color="white"/></div></button> </div> </div> );
const ToggleSwitch = ({ enabled, setEnabled }) => ( <button onClick={() => setEnabled(!enabled)} className={`w-12 h-6 rounded-full flex items-center transition-colors ${enabled ? 'bg-blue-600' : 'bg-gray-600'}`}> <span className={`block w-5 h-5 bg-white rounded-full transform transition-transform ${enabled ? 'translate-x-6' : 'translate-x-1'}`}></span> </button> );

const ShareVideoModal = ({ video, onClose }) => {
    const externalApps = [
        { name: 'WhatsApp', icon: <div className="w-12 h-12 bg-green-500 rounded-full"></div> },
        { name: 'Instagram', icon: <div className="w-12 h-12 bg-gradient-to-br from-yellow-400 via-red-500 to-purple-600 rounded-full"></div> },
        { name: 'X', icon: <div className="w-12 h-12 bg-black border border-gray-600 rounded-full flex items-center justify-center"><X size={24} className="text-white"/></div> },
        { name: 'Copiar', icon: <div className="w-12 h-12 bg-gray-600 rounded-full flex items-center justify-center"><LinkIcon size={24} className="text-white"/></div> },
    ];
    return (
        <div className="fixed inset-0 bg-black bg-opacity-60 z-50 flex items-end" onClick={onClose}>
            <div className="bg-gray-800 w-full rounded-t-2xl p-4 text-white" onClick={e => e.stopPropagation()}>
                <div className="w-10 h-1 bg-gray-600 rounded-full mx-auto mb-4"></div>
                <h3 className="text-lg font-bold text-center mb-4">Compartir video</h3>
                <p className="text-sm text-gray-400 mb-4">Enviar a amigos en Hype</p>
                <div className="flex space-x-4 overflow-x-auto scrollbar-hide pb-4">
                    {mockHypeFriends.map(friend => (
                        <div key={friend.id} className="flex flex-col items-center flex-shrink-0 w-20">
                            <img src={friend.profilePic} className="w-14 h-14 rounded-full mb-2"/>
                            <p className="text-xs text-center truncate w-full">{friend.username}</p>
                            <button className="mt-1 bg-blue-600 text-white text-xs font-bold px-3 py-1 rounded-full">Enviar</button>
                        </div>
                    ))}
                </div>
                <div className="border-t border-gray-700 my-4"></div>
                <p className="text-sm text-gray-400 mb-4">Compartir en otras apps</p>
                <div className="flex justify-around pb-4">
                    {externalApps.map(app => (
                        <div key={app.name} className="flex flex-col items-center">
                            {app.icon}
                            <p className="text-xs mt-2">{app.name}</p>
                        </div>
                    ))}
                </div>
            </div>
        </div>
    );
};

// --- PANTALLAS PRINCIPALES ---

const HomeScreen = ({ videos, handleVote, userVote, canVote, onNavigate, likedVideoIds, savedVideoIds, handleLike, handleSave, handleShare, isRevealTimePassed }) => ( <div className="h-full w-full bg-black relative"> <button onClick={() => onNavigate('search')} className="absolute top-4 left-4 bg-black bg-opacity-50 p-2 rounded-full z-20 hover:bg-opacity-75 transition-colors"><Search size={24} className="text-white"/></button> <div className="h-full w-full snap-y snap-mandatory overflow-y-scroll scrollbar-hide">{videos.map(video => <VideoPlayer key={video.id} video={video} onVote={handleVote} canVote={canVote} isVoted={userVote === video.id} onLike={handleLike} isLiked={likedVideoIds.has(video.id)} onSave={handleSave} isSaved={savedVideoIds.has(video.id)} onShare={handleShare} isRevealTimePassed={isRevealTimePassed} />)}</div> <CountdownTimer /> </div> );
const SearchScreen = ({ onBack }) => ( <div className="h-full w-full bg-black text-white p-4 flex flex-col"> <div className="flex items-center mb-6"><button onClick={onBack} className="mr-2"><ChevronLeft size={24} /></button><div className="relative flex-1"><Search size={20} className="absolute left-3 top-1/2 -translate-y-1/2 text-gray-400"/><input type="text" placeholder="Buscar videos, usuarios..." className="w-full bg-gray-800 text-white pl-10 pr-4 py-2 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"/></div></div> <div className="flex-1"><h2 className="text-lg font-bold mb-4 text-gray-300">Tendencias</h2><div className="flex flex-col space-y-3">{mockTrending.map((trend, index) => (<button key={index} className="flex items-center space-x-3 p-2 hover:bg-gray-800 rounded-md transition-colors text-left"><div className="p-2 bg-gray-700 rounded-full"><Hash size={16} className="text-gray-400"/></div><span className="font-semibold">{trend}</span></button>))}</div></div> </div> );
const WalletScreen = ({ onBack }) => ( <div className="h-full w-full bg-black text-white p-4 flex flex-col"> <div className="flex items-center mb-4"><button onClick={onBack} className="mr-4"><ChevronLeft size={24} /></button><h1 className="text-xl font-bold">Billetera</h1></div> <div className="flex-1 overflow-y-auto scrollbar-hide"> <div className="bg-gradient-to-br from-blue-600 to-purple-700 p-6 rounded-2xl text-center mb-6 shadow-lg shadow-blue-500/20"><p className="text-sm text-blue-200">Balance Total</p><p className="text-4xl font-bold mt-1">12,500 Puntos</p></div> <div><h2 className="text-lg font-bold mb-3 flex items-center"><Gift size={20} className="mr-2 text-blue-400"/>Canjear Puntos</h2><div className="space-y-3">{mockRewards.redeem.map(item => (<div key={item.id} className="bg-gray-800 p-4 rounded-lg flex items-center justify-between"><div className="flex items-center"><img src={item.icon} className="w-10 h-10 rounded-md mr-4"/><p className="font-semibold">{item.title}</p></div><button className="bg-blue-600 text-white text-sm font-bold px-3 py-1.5 rounded-md">{item.points.toLocaleString()} pts</button></div>))}</div></div> <div className="mt-8"><h2 className="text-lg font-bold mb-3 flex items-center"><Percent size={20} className="mr-2 text-blue-400"/>Descuentos Exclusivos</h2><div className="grid grid-cols-2 gap-4">{mockRewards.discounts.map(item => (<div key={item.id} className="bg-gray-800 p-4 rounded-lg text-center"><img src={item.icon} className="w-16 h-16 rounded-lg mx-auto mb-2"/><p className="font-semibold text-sm">{item.title}</p><p className="text-xs text-gray-400">{item.partner}</p></div>))}</div></div> </div> </div> );
const SettingsPanel = ({ isOpen, onClose, onNavigate }) => ( <div className={`fixed inset-0 z-40 transition-opacity ${isOpen ? 'bg-black bg-opacity-50' : 'bg-transparent pointer-events-none'}`} onClick={onClose}> <div className={`fixed top-0 right-0 h-full w-72 bg-gray-900 text-white z-50 transform transition-transform shadow-2xl ${isOpen ? 'translate-x-0' : 'translate-x-full'}`} onClick={e => e.stopPropagation()}> <div className="p-4 border-b border-gray-700"><h2 className="text-xl font-bold">Menú</h2></div> <div className="flex flex-col justify-between h-[calc(100%-57px)]"> <div> <button onClick={() => { onNavigate('wallet'); onClose(); }} className="flex items-center w-full text-left p-4 hover:bg-gray-800"><Wallet size={20} className="mr-3 text-blue-400"/>Billetera</button> <button onClick={() => { onNavigate('settings'); onClose(); }} className="flex items-center w-full text-left p-4 hover:bg-gray-800"><Settings2 size={20} className="mr-3 text-blue-400"/>Ajustes y Privacidad</button> </div> <div className="p-4 border-t border-gray-700"> <p className="text-sm text-gray-400 mb-2">Tu código Hype</p> <div className="bg-white p-2 rounded-lg flex items-center justify-center"><QrCode size={144} className="text-black"/></div> </div> </div> </div> </div> );
const SettingsScreen = ({ onBack }) => { const SettingItem = ({ icon, text }) => (<button className="flex justify-between items-center w-full text-left p-3 hover:bg-gray-800 rounded-lg"> <div className="flex items-center"> {icon} <span className="ml-4">{text}</span> </div> <ChevronLeft size={20} className="text-gray-500 -rotate-180" /> </button>); const SectionTitle = ({ text }) => (<h3 className="text-gray-400 text-sm font-bold px-3 mt-4 mb-2">{text.toUpperCase()}</h3>); return ( <div className="h-full w-full bg-black text-white flex flex-col"> <div className="flex items-center p-4 border-b border-gray-800"><button onClick={onBack} className="mr-4"><ChevronLeft size={24} /></button><h1 className="text-xl font-bold">Ajustes y Privacidad</h1></div> <div className="flex-1 overflow-y-auto scrollbar-hide pb-4"> <SectionTitle text="Cuenta" /> <SettingItem icon={<User size={20}/>} text="Cuenta" /> <SettingItem icon={<Lock size={20}/>} text="Privacidad" /> <SettingItem icon={<Shield size={20}/>} text="Seguridad y permisos" /> <SettingItem icon={<Share2 size={20}/>} text="Compartir perfil" /> <SectionTitle text="Contenido y pantalla" /> <SettingItem icon={<Bell size={20}/>} text="Notificaciones" /> <SettingItem icon={<Tv size={20}/>} text="LIVE" /> <SettingItem icon={<Music size={20}/>} text="Música" /> <SettingItem icon={<Activity size={20}/>} text="Centro de actividades" /> <SettingItem icon={<SlidersHorizontal size={20}/>} text="Preferencias de contenido" /> <SettingItem icon={<UserMinus size={20}/>} text="Limitar a los espectadores" /> <SettingItem icon={<Megaphone size={20}/>} text="Anuncios" /> <SectionTitle text="Caché y datos móviles" /> <SettingItem icon={<Download size={20}/>} text="Vídeos sin conexión" /> <SettingItem icon={<Trash2 size={20}/>} text="Liberar espacio" /> <SettingItem icon={<WifiOff size={20}/>} text="Ahorro de datos" /> <SectionTitle text="Ayuda e información" /> <SettingItem icon={<Flag size={20}/>} text="Informar de un problema" /> <SettingItem icon={<HelpCircle size={20}/>} text="Ayuda" /> <SettingItem icon={<Info size={20}/>} text="Términos y condiciones" /> <SectionTitle text="Inicio de sesión" /> <SettingItem icon={<RefreshCw size={20}/>} text="Cambiar de cuenta" /> <SettingItem icon={<LogOut size={20}/>} text="Cerrar sesión" /> </div> </div> ); };
const ProfileViewsScreen = ({ onBack }) => ( <div className="h-full w-full bg-black text-white p-4 flex flex-col"> <div className="flex items-center mb-4"><button onClick={onBack} className="mr-4"><ChevronLeft size={24} /></button><h1 className="text-xl font-bold">Vistas del Perfil</h1></div> <p className="text-sm text-gray-400 mb-4">Usuarios que han visto tu perfil en los últimos 30 días.</p> <div className="flex-1 overflow-y-auto scrollbar-hide"> {mockProfileViewers.map(viewer => ( <div key={viewer.id} className="flex items-center justify-between p-3 hover:bg-gray-800 rounded-lg"> <div className="flex items-center"><img src={viewer.profilePic} className="w-12 h-12 rounded-full mr-4"/><p className="font-semibold">{viewer.username}</p></div> <button className="bg-blue-600 text-white text-sm font-bold px-4 py-1.5 rounded-md">Seguir</button> </div> ))} </div> </div> );
const SearchFriendsScreen = ({ onBack }) => ( <div className="h-full w-full bg-black text-white p-4 flex flex-col"> <div className="flex items-center mb-6"><button onClick={onBack} className="mr-2"><ChevronLeft size={24} /></button><div className="relative flex-1"><Search size={20} className="absolute left-3 top-1/2 -translate-y-1/2 text-gray-400"/><input type="text" placeholder="Buscar amigos..." className="w-full bg-gray-800 text-white pl-10 pr-4 py-2 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"/></div></div> <div className="flex-1 overflow-y-auto scrollbar-hide"> <h2 className="text-lg font-bold mb-4 text-gray-300">Gente recomendada</h2> {mockRecommendedUsers.map(user => ( <div key={user.id} className="flex items-center justify-between p-3 hover:bg-gray-800 rounded-lg"> <div className="flex items-center"><img src={`https://placehold.co/100x100/444/fff?text=${user.username.charAt(1).toUpperCase()}`} className="w-12 h-12 rounded-full mr-4"/><div><p className="font-semibold">{user.username}</p><p className="text-sm text-gray-400">{user.bio}</p></div></div> <button className="bg-blue-600 text-white text-sm font-bold px-4 py-1.5 rounded-md">Seguir</button> </div> ))} </div> </div> );
const ShareProfileModal = ({ user, onClose }) => { const [copied, setCopied] = useState(false); const profileLink = `hype.app/${user.username}`; const handleCopy = () => { try { const textArea = document.createElement("textarea"); textArea.value = profileLink; document.body.appendChild(textArea); textArea.focus(); textArea.select(); document.execCommand('copy'); document.body.removeChild(textArea); setCopied(true); setTimeout(() => setCopied(false), 2000); } catch (err) { console.error('Fallback: Oops, unable to copy', err); } }; return ( <div className="fixed inset-0 bg-black bg-opacity-70 z-50 flex items-center justify-center" onClick={onClose}> <div className="bg-gray-800 rounded-2xl p-6 w-11/12 max-w-sm text-center" onClick={e => e.stopPropagation()}> <h2 className="text-xl font-bold mb-4">Compartir Perfil</h2> <div className="bg-white p-4 rounded-lg inline-block mb-4"><QrCode size={160} className="text-black"/></div> <p className="font-bold text-lg">{user.username}</p> <div className="flex items-center bg-gray-700 p-2 rounded-lg my-4"> <p className="flex-1 text-gray-300 text-sm truncate">{profileLink}</p> <button onClick={handleCopy} className="bg-blue-600 text-white font-bold px-3 py-1 rounded-md ml-2">{copied ? '¡Copiado!' : 'Copiar'}</button> </div> </div> </div> ); };

const ProfileScreen = ({ onNavigate, isRevealTimePassed }) => {
    const [user, setUser] = useState(mockUser);
    const [activeTab, setActiveTab] = useState('videos');
    const [isSettingsOpen, setIsSettingsOpen] = useState(false);
    const [showShareModal, setShowShareModal] = useState(false);
    const userVideos = mockVideos.filter(v => v.user === user.username);

    const renderTabContent = () => {
        let items = [];
        switch (activeTab) {
            case 'videos': items = userVideos; break;
            case 'voted': items = mockProfileTabs.voted; break;
            case 'shared': items = mockProfileTabs.shared; break;
            case 'saved': items = mockProfileTabs.saved; break;
            case 'drafts': items = mockProfileTabs.drafts; break;
            default: return null;
        }
        return ( <div className="grid grid-cols-3 gap-0.5"> {items.map(video => ( <div key={video.id} className="bg-gray-800 aspect-square bg-cover bg-center relative" style={{backgroundImage: `url(${video.videoUrl})`}}> {activeTab === 'videos' && (<> <div className="absolute bottom-1 left-1 bg-black bg-opacity-50 text-white text-xs px-1 py-0.5 rounded flex items-center"><Trophy size={10} className="mr-1 text-yellow-400"/> Top #{video.globalRank.toLocaleString()}</div> <div className="absolute bottom-1 right-1 bg-black bg-opacity-50 text-white text-xs px-1.5 py-0.5 rounded flex items-center space-x-1">{isRevealTimePassed ? <> <Eye size={12}/> <span>{video.views.toLocaleString()}</span> </> : <CountdownTimer isSmall={true} />}</div> </>)} </div> ))} </div> );
    };

    const TabButton = ({ tabName, icon, isPrivate }) => ( <button onClick={() => setActiveTab(tabName)} className={`flex-1 pb-2 border-b-2 flex justify-center items-center space-x-1 ${activeTab === tabName ? 'border-white text-white' : 'border-transparent text-gray-500'}`}> {icon} {isPrivate && <Lock size={10}/>} </button> );

    return (
        <div className="h-full w-full bg-black text-white flex flex-col">
            <div className="p-4 bg-black flex justify-between items-center"> <button onClick={() => onNavigate('searchFriends')}><User size={24}/><Plus size={12} className="-ml-2 -mt-4 bg-blue-500 rounded-full p-0.5"/></button> <div className="flex items-center space-x-4"> <button onClick={() => onNavigate('profileViews')}><Eye size={24}/></button> <button onClick={() => setShowShareModal(true)}><Share2 size={24}/></button> <button onClick={() => setIsSettingsOpen(true)}><Menu size={24}/></button> </div> </div>
            <div className="p-4 pt-0 flex-1 flex flex-col overflow-y-auto scrollbar-hide">
                <div className="flex flex-col items-center text-center"> <img src={user.profilePic} alt="Profile" className="w-24 h-24 rounded-full border-2 border-blue-500"/> <h2 className="text-xl font-bold mt-2">{user.username}</h2> </div>
                <div className="flex justify-around text-center my-4"> <div><span className="font-bold">{user.following}</span><p className="text-sm text-gray-400">Siguiendo</p></div> <div><span className="font-bold">{user.followers.toLocaleString()}</span><p className="text-sm text-gray-400">Seguidores</p></div> <div><span className="font-bold">{user.votes.toLocaleString()}</span><p className="text-sm text-gray-400">Votos</p></div> </div>
                <p className="text-sm my-2 text-center">{user.bio}</p>
                <div className="text-center"><a href={`https://${user.link}`} target="_blank" rel="noopener noreferrer" className="text-blue-400 text-sm font-semibold flex items-center justify-center space-x-1"><LinkIcon size={14} /><span>{user.link}</span></a></div>
                <div className="flex space-x-2 mt-4"><button onClick={() => onNavigate('editProfile')} className="flex-1 bg-gray-800 text-white py-2 rounded-md text-sm font-semibold hover:bg-gray-700">Editar Perfil</button></div>
                <div className="flex border-b border-gray-700 mt-4">
                    <TabButton tabName="videos" icon={<Video className="mx-auto"/>} />
                    <TabButton tabName="voted" icon={<Heart className="mx-auto"/>} isPrivate={true} />
                    <TabButton tabName="shared" icon={<Send className="mx-auto"/>} />
                    <TabButton tabName="saved" icon={<Bookmark className="mx-auto"/>} isPrivate={true} />
                    <TabButton tabName="drafts" icon={<FileVideo className="mx-auto"/>} isPrivate={true} />
                </div>
                {renderTabContent()}
            </div>
            <SettingsPanel isOpen={isSettingsOpen} onClose={() => setIsSettingsOpen(false)} onNavigate={onNavigate} />
            {showShareModal && <ShareProfileModal user={user} onClose={() => setShowShareModal(false)} />}
        </div>
    );
}

// --- OTRAS PANTALLAS ---
const FriendsScreen = () => ( <div className="h-full w-full bg-black text-white flex flex-col"> <div className="p-4 border-b border-gray-800"> <h1 className="text-2xl font-bold">Amigos</h1> <div className="mt-4"> <h2 className="text-sm font-bold text-gray-400 mb-2">Historias</h2> <div className="flex space-x-4 overflow-x-auto scrollbar-hide"> <div className="flex flex-col items-center space-y-1"> <div className="w-16 h-16 rounded-full bg-gray-700 flex items-center justify-center"><Camera size={24}/></div> <p className="text-xs">Tu historia</p> </div> {mockFriendsContent.stories.map(story => ( <div key={story.id} className="flex flex-col items-center space-y-1"> <div className={`w-16 h-16 rounded-full p-0.5 ${!story.seen ? 'bg-gradient-to-tr from-yellow-400 to-purple-500' : 'bg-gray-700'}`}> <img src={story.img} className="w-full h-full rounded-full border-2 border-black"/> </div> <p className="text-xs">{story.user}</p> </div> ))} </div> </div> </div> <div className="flex-1 overflow-y-auto scrollbar-hide"> {mockFriendsContent.live.length > 0 && ( <div className="p-4"> <h2 className="text-sm font-bold text-gray-400 mb-2">En Directo</h2> {mockFriendsContent.live.map(live => ( <div key={live.id} className="bg-gray-800 rounded-lg p-3 flex items-center justify-between"> <div className="flex items-center space-x-3"> <img src={`https://placehold.co/50x50/ff4500/ffffff?text=${live.user.charAt(1).toUpperCase()}`} className="w-10 h-10 rounded-full"/> <div> <p className="font-bold">{live.user}</p> <p className="text-xs text-gray-300">{live.title}</p> </div> </div> <button className="bg-red-600 text-white px-3 py-1 text-sm rounded-md font-semibold flex items-center space-x-1"><Radio size={14}/><span>Unirse</span></button> </div> ))} </div> )} <div className="h-[calc(100vh-200px)] w-full bg-black snap-y snap-mandatory overflow-y-scroll scrollbar-hide"> {mockFriendsContent.videos.map(video => <VideoPlayer key={video.id} video={video} isFriendFeed={true} />)} </div> </div> </div> );
const EditProfileScreen = ({ onBack }) => { const [isPrivate, setIsPrivate] = useState(mockUser.isPrivate); return ( <div className="h-full w-full bg-gray-900 text-white p-4 flex flex-col"> <div className="flex items-center mb-6"> <button onClick={onBack} className="mr-4"><ChevronLeft size={24} /></button> <h1 className="text-xl font-bold">Editar Perfil</h1> </div> <div className="flex-1 overflow-y-auto"> <div className="text-center mb-6"> <img src={mockUser.profilePic} className="w-24 h-24 rounded-full mx-auto border-2 border-blue-500"/> <button className="text-blue-400 font-semibold text-sm mt-2">Cambiar foto</button> </div> <div className="space-y-4"> <div><label className="text-sm text-gray-400">Nombre de usuario</label><input type="text" defaultValue={mockUser.username} className="w-full bg-gray-800 p-2 rounded-md mt-1"/></div> <div><label className="text-sm text-gray-400">Biografía</label><textarea defaultValue={mockUser.bio} className="w-full bg-gray-800 p-2 rounded-md mt-1 h-24"></textarea></div> <div><label className="text-sm text-gray-400">Enlace</label><input type="text" defaultValue={mockUser.link} className="w-full bg-gray-800 p-2 rounded-md mt-1"/></div> </div> <div className="flex justify-between items-center bg-gray-800 p-3 rounded-md mt-6"> <div> <h3 className="font-semibold">Modo Privado</h3> <p className="text-xs text-gray-400">Solo tus seguidores podrán ver tus videos y perfil.</p> </div> <ToggleSwitch enabled={isPrivate} setEnabled={setIsPrivate} /> </div> </div> <button onClick={onBack} className="w-full bg-blue-600 text-white font-bold py-3 rounded-lg mt-4 hover:bg-blue-700">Guardar</button> </div> );};
const RankingScreen = ({ onBack }) => { const [activeTab, setActiveTab] = useState('daily'); return (<div className="h-full w-full bg-gray-900 text-white p-4 flex flex-col"><button onClick={onBack} className="self-start text-gray-400 hover:text-white mb-2"><X size={24} /></button><div className="text-center mb-4"><Trophy size={48} className="text-blue-400 mx-auto mb-2" /><h1 className="text-3xl font-bold">Ranking de Hype</h1></div><div className="flex justify-center bg-gray-800 rounded-lg p-1 mb-4"><button onClick={() => setActiveTab('daily')} className={`flex-1 py-2 px-4 rounded-md text-sm font-bold ${activeTab === 'daily' ? 'bg-blue-600' : ''}`}>Día</button><button onClick={() => setActiveTab('weekly')} className={`flex-1 py-2 px-4 rounded-md text-sm font-bold ${activeTab === 'weekly' ? 'bg-blue-600' : ''}`}>Semana</button><button onClick={() => setActiveTab('monthly')} className={`flex-1 py-2 px-4 rounded-md text-sm font-bold ${activeTab === 'monthly' ? 'bg-blue-600' : ''}`}>Mes</button></div><div className="flex-1 overflow-y-auto scrollbar-hide">{mockRankings[activeTab].map((v, i) => <div key={v.id} className="flex items-center p-3 bg-gray-800 rounded-lg mb-3"><span className={`text-2xl font-bold w-12 ${i === 0 ? 'text-yellow-400' : i === 1 ? 'text-gray-300' : 'text-yellow-600'}`}>#{i + 1}</span><div className="flex-1"><p className="font-bold">{v.user}</p><p className="text-sm text-gray-400 truncate">{v.description}</p></div><div className="text-right"><p className="font-bold text-blue-400">{v.votes.toLocaleString()}</p><p className="text-xs text-gray-500">votos</p></div></div>)}</div></div>);};
const UploadScreen = ({ onBack }) => ( <div className="h-full w-full bg-gray-900 text-white p-6 flex flex-col items-center justify-center text-center relative"><button onClick={onBack} className="absolute top-6 right-6 text-gray-400 hover:text-white"><X size={24} /></button><Upload size={64} className="text-blue-400 mb-4" /><h1 className="text-3xl font-bold mb-2">Subir Video</h1><p className="text-gray-400 mb-8">Graba o selecciona un video (máx. 60s).</p><button className="bg-blue-600 text-white font-bold py-3 px-8 rounded-lg hover:bg-blue-700">Seleccionar</button><p className="my-4 text-gray-400">o</p><button className="bg-gray-700 text-white font-bold py-3 px-8 rounded-lg hover:bg-gray-600">Grabar</button></div>);
const InboxScreen = () => ( <div className="h-full w-full bg-black text-white p-4 flex flex-col"><div className="flex justify-between items-center mb-4"><h1 className="text-2xl font-bold">Bandeja de Entrada</h1><button><Edit size={20}/></button></div><div className="flex-1 overflow-y-auto">{['@amigo1', '@gamerpro', '@viajandoporelmundo'].map(f => <div key={f} className="flex items-center p-3 hover:bg-gray-900 rounded-lg"><img src={`https://placehold.co/50x50/222/fff?text=${f.charAt(1).toUpperCase()}`} className="w-12 h-12 rounded-full mr-4"/><div className="flex-1"><p className="font-semibold">{f}</p><p className="text-sm text-gray-400">Ok, nos vemos luego! · 1h</p></div></div>)}</div></div>);

// --- COMPONENTE PRINCIPAL DE LA APP ---

export default function App() {
  const [currentScreen, setCurrentScreen] = useState('home');
  const [userVote, setUserVote] = useState(null);
  const [canVote, setCanVote] = useState(true);
  const [showUpload, setShowUpload] = useState(false);
  const [isRevealTimePassed, setIsRevealTimePassed] = useState(false);
  const [likedVideoIds, setLikedVideoIds] = useState(new Set());
  const [savedVideoIds, setSavedVideoIds] = useState(new Set());
  const [videoToShare, setVideoToShare] = useState(null);
  
  const [db, setDb] = useState(null);
  const [auth, setAuth] = useState(null);
  const [userId, setUserId] = useState(null);
  const [isAuthReady, setIsAuthReady] = useState(false);

  useEffect(() => { const revealTime = new Date(); revealTime.setHours(21, 0, 0, 0); const now = new Date(); setIsRevealTimePassed(now > revealTime); }, []);

  useEffect(() => {
    const app = initializeApp(firebaseConfig); const authInstance = getAuth(app); const dbInstance = getFirestore(app);
    setDb(dbInstance); setAuth(authInstance);
    const unsub = onAuthStateChanged(authInstance, async (user) => {
      if (user) { setUserId(user.uid); setIsAuthReady(true); } 
      else { try { if (initialAuthToken) { await signInWithCustomToken(authInstance, initialAuthToken); } else { await signInAnonymously(authInstance); } } catch (error) { console.error("Auth Error:", error); setIsAuthReady(true); } }
    });
    return () => unsub();
  }, []);

  // FIRESTORE FIX: Use a single document for votes to avoid permission issues with collection queries.
  useEffect(() => {
    if (!isAuthReady || !db || !userId) return;
    
    // Path to a single document that will store all votes for the user.
    const votesDocRef = doc(db, 'artifacts', appId, 'users', userId, 'user_data', 'votes');

    const unsub = onSnapshot(votesDocRef, (docSnap) => {
        const today = new Date().toISOString().split('T')[0];
        if (docSnap.exists()) {
            const votesData = docSnap.data();
            // Check if a vote for today exists in the document's map.
            if (votesData && votesData[today]) {
                setUserVote(votesData[today]);
                setCanVote(false);
            } else {
                setUserVote(null);
                setCanVote(true);
            }
        } else {
            // Document doesn't exist, so no votes yet.
            setUserVote(null);
            setCanVote(true);
        }
    }, (err) => {
        console.error("Vote snapshot error:", err);
    });
    return () => unsub();
  }, [isAuthReady, db, userId]);

  const handleVote = async (videoId) => {
    if (!canVote || !isAuthReady || !db || !userId) return;
    setCanVote(false); setUserVote(videoId);
    try {
        const today = new Date().toISOString().split('T')[0];
        const votesDocRef = doc(db, 'artifacts', appId, 'users', userId, 'user_data', 'votes');
        // Use setDoc with merge to update the map field for the current date
        // without overwriting the entire document.
        await setDoc(votesDocRef, { [today]: videoId }, { merge: true });
    } catch (error) { 
        console.error("Error saving vote: ", error); 
        // Revert UI state on failure
        setCanVote(true); 
        setUserVote(null); 
    }
  };
  
  const handleLike = (videoId) => { setLikedVideoIds(prev => { const newSet = new Set(prev); if (newSet.has(videoId)) { newSet.delete(videoId); } else { newSet.add(videoId); } return newSet; }); };
  const handleSave = (videoId) => { setSavedVideoIds(prev => { const newSet = new Set(prev); if (newSet.has(videoId)) { newSet.delete(videoId); } else { newSet.add(videoId); } return newSet; }); };
  const handleShare = (video) => { setVideoToShare(video); };
  const handleNavigation = (screen) => setCurrentScreen(screen);

  const renderScreen = () => {
    if (showUpload) return <UploadScreen onBack={() => setShowUpload(false)} />;
    
    switch (currentScreen) {
      case 'home': return <HomeScreen videos={mockVideos} handleVote={handleVote} userVote={userVote} canVote={canVote} onNavigate={handleNavigation} likedVideoIds={likedVideoIds} savedVideoIds={savedVideoIds} handleLike={handleLike} handleSave={handleSave} handleShare={handleShare} isRevealTimePassed={isRevealTimePassed} />;
      case 'search': return <SearchScreen onBack={() => setCurrentScreen('home')} />;
      case 'friends': return <FriendsScreen />;
      case 'inbox': return <InboxScreen />;
      case 'profile': return <ProfileScreen onNavigate={handleNavigation} isRevealTimePassed={isRevealTimePassed} />;
      case 'editProfile': return <EditProfileScreen onBack={() => setCurrentScreen('profile')} />;
      case 'wallet': return <WalletScreen onBack={() => setCurrentScreen('profile')} />;
      case 'ranking': return <RankingScreen onBack={() => setCurrentScreen('profile')} />;
      case 'settings': return <SettingsScreen onBack={() => setCurrentScreen('profile')} />;
      case 'profileViews': return <ProfileViewsScreen onBack={() => setCurrentScreen('profile')} />;
      case 'searchFriends': return <SearchFriendsScreen onBack={() => setCurrentScreen('profile')} />;
      default: return <HomeScreen videos={mockVideos} handleVote={handleVote} userVote={userVote} canVote={canVote} onNavigate={handleNavigation} likedVideoIds={likedVideoIds} savedVideoIds={savedVideoIds} handleLike={handleLike} handleSave={handleSave} handleShare={handleShare} isRevealTimePassed={isRevealTimePassed} />;
    }
  };

  return (
    <div className="h-screen w-screen bg-black font-sans flex flex-col">
      <main className="flex-1 overflow-hidden">{renderScreen()}</main>
      
      {videoToShare && <ShareVideoModal video={videoToShare} onClose={() => setVideoToShare(null)} />}

      {!showUpload && !['editProfile', 'wallet', 'ranking', 'search', 'settings', 'profileViews', 'searchFriends'].includes(currentScreen) && (
        <footer className="w-full bg-black">
          <nav className="flex justify-around items-center h-16 text-gray-400">
            <button onClick={() => setCurrentScreen('home')} className={`flex flex-col items-center transition-colors ${currentScreen === 'home' ? 'text-white' : ''}`}><Home size={28} /><span className="text-xs font-bold">Inicio</span></button>
            <button onClick={() => setCurrentScreen('friends')} className={`flex flex-col items-center transition-colors ${currentScreen === 'friends' ? 'text-white' : ''}`}><Users size={28} /><span className="text-xs font-bold">Amigos</span></button>
            <button onClick={() => setShowUpload(true)} className="w-14 h-10 bg-gradient-to-r from-purple-600 to-blue-600 rounded-2xl flex items-center justify-center text-white shadow-lg shadow-blue-500/30 hover:scale-105 transition-transform"><Plus size={28} /></button>
            <button onClick={() => setCurrentScreen('inbox')} className={`flex flex-col items-center transition-colors ${currentScreen === 'inbox' ? 'text-white' : ''}`}><Inbox size={28} /><span className="text-xs font-bold">Bandeja</span></button>
            <button onClick={() => setCurrentScreen('profile')} className={`flex flex-col items-center transition-colors ${currentScreen === 'profile' ? 'text-white' : ''}`}><User size={28} /><span className="text-xs font-bold">Perfil</span></button>
          </nav>
        </footer>
      )}
    </div>
  );
}
