// package.json
{
  "name": "neela-mozhi",
  "version": "1.0.0",
  "description": "Neela Mozhi - Conversational Malayalam Learning App",
  "private": true,
  "dependencies": {
    "@capacitor/android": "^5.0.0",
    "@capacitor/core": "^5.0.0",
    "@capacitor/ios": "^5.0.0",
    "@supabase/supabase-js": "^2.39.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.22.0",
    "react-scripts": "5.0.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": ["react-app"]
  },
  "browserslist": {
    "production": [">0.2%", "not dead", "not op_mini all"],
    "development": ["last 1 chrome version", "last 1 firefox version", "last 1 safari version"]
  }
}

// capacitor.config.json
{
  "appId": "ai.aksharam.neelamozhi",
  "appName": "Neela Mozhi",
  "webDir": "build",
  "server": {
    "androidScheme": "https"
  }
}
// .env.example
REACT_APP_SUPABASE_URL=https://YOUR_PROJECT_ID.supabase.co
REACT_APP_SUPABASE_ANON_KEY=YOUR_ANON_KEY_HERE
REACT_APP_AI_API_KEY=YOUR_AI_KEY_HERE

// public/index.html
<!DOCTYPE html>
<html lang="ml">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#1a3c5e" />
    <meta name="description" content="Neela Mozhi - Speak Malayalam Confidently with AI" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Noto+Sans+Malayalam:wght@400;600;700&family=Inter:wght@400;500;600;700&display=swap"
      rel="stylesheet"
    />
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <title>Neela Mozhi | നീല മൊഴി</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
// public/manifest.json
{
  "short_name": "Neela Mozhi",
  "name": "Neela Mozhi - Malayalam Learning",
  "icons": [
    {
      "src": "favicon.ico",
      "sizes": "64x64 32x32 24x24 16x16",
      "type": "image/x-icon"
    }
  ],
  "start_url": ".",
  "display": "standalone",
  "theme_color": "#1a3c5e",
  "background_color": "#ffffff"
}

// src/supabaseClient.js

import { createClient } from '@supabase/supabase-js'

const supabaseUrl = process.env.REACT_APP_SUPABASE_URL
const supabaseAnonKey = process.env.REACT_APP_SUPABASE_ANON_KEY

export const supabase = createClient(supabaseUrl, supabaseAnonKey)

// src/index.js
import React from 'react'
import ReactDOM from 'react-dom/client'
import './index.css'
import App from './App'

const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)

// src/index.css
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --color-primary: #1a3c5e;
  --color-accent: #f4a261;
  --color-light: #e8f4fd;
  --color-white: #ffffff;
  --color-bg: #f0f4f8;
  --font-main: 'Inter', 'Segoe UI', sans-serif;
  --font-malayalam: 'Noto Sans Malayalam', sans-serif;
  --radius-card: 16px;
  --radius-btn: 12px;
  --shadow-card: 0 2px 12px rgba(0,0,0,0.08);
}

body {
  font-family: var(--font-main);
  background-color: var(--color-bg);
  color: var(--color-primary);
  -webkit-font-smoothing: antialiased;
  min-height: 100vh;
}

#root {
  max-width: 480px;
  margin: 0 auto;
  min-height: 100vh;
  background: var(--color-white);
}

.malayalam {
  font-family: var(--font-malayalam);
}

.screen {
  padding: 20px;
  padding-bottom: 90px;
  min-height: 100vh;
}

.screen-header {
  text-align: center;
  padding: 20px 0 16px;
}

.screen-header h1 {
  font-size: 1.7rem;
  color: var(--color-primary);
  font-weight: 700;
}

.malayalam-title {
  font-size: 1.2rem;
  color: var(--color-accent);
  font-family: var(--font-malayalam);
  margin-top: 4px;
}

.screen-header p {
  color: #666;
  margin-top: 8px;
  font-size: 0.92rem;
}

.btn-primary {
  background: var(--color-primary);
  color: white;
  border: none;
  padding: 14px 28px;
  border-radius: var(--radius-btn);
  font-size: 1rem;
  cursor: pointer;
  width: 100%;
  margin: 8px 0;
  font-weight: 600;
  transition: opacity 0.2s;
}

.btn-primary:hover { opacity: 0.88; }
.btn-primary:disabled { opacity: 0.5; cursor: not-allowed; }

.btn-accent {
  background: var(--color-accent);
  color: white;
  border: none;
  padding: 14px 28px;
  border-radius: var(--radius-btn);
  font-size: 1rem;
  cursor: pointer;
  width: 100%;
  margin: 8px 0;
  font-weight: 600;
  transition: opacity 0.2s;
}

.btn-accent:hover { opacity: 0.88; }

.card {
  background: var(--color-white);
  border-radius: var(--radius-card);
  padding: 20px;
  box-shadow: var(--shadow-card);
  margin: 12px 0;
  border: 2px solid transparent;
}

.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  max-width: 480px;
  background: white;
  border-top: 1px solid #e0e0e0;
  display: flex;
  box-shadow: 0 -2px 12px rgba(0,0,0,0.08);
  z-index: 100;
}

.nav-btn {
  flex: 1;
  padding: 10px 0;
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 3px;
  transition: opacity 0.2s;
}

.nav-btn:hover { opacity: 0.75; }

.nav-icon { font-size: 1.4rem; }

.nav-label {
  font-size: 0.7rem;
  color: #999;
  font-weight: 500;
}

.nav-btn.active .nav-label {
  color: #1a3c5e;
  font-weight: 700;
}

// src/App.js
* { box-sizing: border-box; }

// src/screens/LoginScreen.js
import React, { useState } from 'react'
import { supabase } from '../supabaseClient'

export default function LoginScreen() {
  const [email, setEmail] = useState('')
  const [password, setPassword] = useState('')
  const [isSignUp, setIsSignUp] = useState(false)
  const [loading, setLoading] = useState(false)
  const [message, setMessage] = useState('')

  async function handleAuth(e) {
    e.preventDefault()
    setLoading(true)
    setMessage('')
    const { error } = isSignUp
      ? await supabase.auth.signUp({ email, password })
      : await supabase.auth.signInWithPassword({ email, password })
    if (error) setMessage(error.message)
    else if (isSignUp) setMessage('Check your email to confirm your account!')
    setLoading(false)
  }

  return (
    <div style={{
      minHeight:'100vh',
      background:'linear-gradient(135deg,#1a3c5e,#2980b9)',
      display:'flex', alignItems:'center', justifyContent:'center', padding:'20px'
    }}>
      <div style={{
        background:'white', borderRadius:'24px', padding:'36px',
        width:'100%', maxWidth:'400px', boxShadow:'0 20px 60px rgba(0,0,0,0.3)'
      }}>
        <div style={{textAlign:'center', marginBottom:'32px'}}>
          <div style={{fontSize:'3rem'}}> </div>
          <h1 style={{color:'#1a3c5e', marginTop:'10px', fontSize:'1.8rem'}}>Neela Mozhi</h1>
          <div className="malayalam" style={{color:'#f4a261', fontSize:'1.2rem', marginTop:'4px'}}>
            നീല മൊഴി
          </div>
          <p style={{color:'#888', marginTop:'8px', fontSize:'0.9rem'}}>
            Speak Malayalam Confidently with AI
          </p>
        </div>
        <form onSubmit={handleAuth}>
          <input
            type="email"
            placeholder="Email address"
            value={email}
            onChange={e => setEmail(e.target.value)}
            required
            style={{
              width:'100%', padding:'14px 16px', borderRadius:'12px',
              border:'2px solid #e0e0e0', fontSize:'1rem',
              marginBottom:'14px', outline:'none'
            }}
          />
          <input
            type="password"
            placeholder="Password"
            value={password}
            onChange={e => setPassword(e.target.value)}
            required
            style={{
              width:'100%', padding:'14px 16px', borderRadius:'12px',
              border:'2px solid #e0e0e0', fontSize:'1rem',
              marginBottom:'14px', outline:'none'
            }}
          />
          {message && (
            <p style={{color:'#e74c3c', marginBottom:'12px', fontSize:'0.9rem'}}>{message}</p>
          )}
          <button type="submit" className="btn-primary" disabled={loading}>
            {loading ? 'Please wait...' : isSignUp ? 'Create Account' : 'Sign In'}
          </button>
        </form>
        <button
          onClick={() => setIsSignUp(!isSignUp)}
          style={{
            width:'100%', marginTop:'14px', background:'none',
            border:'none', color:'#1a3c5e', cursor:'pointer',
            fontSize:'0.9rem', textDecoration:'underline'
          }}
        >
          {isSignUp ? 'Already have an account? Sign in' : "Don't have an account? Sign up"}
        </button>
      </div>
    </div>
  )
}

// src/screens/HomeScreen.js
import React from 'react'
import { useNavigate } from 'react-router-dom'

const scenarios = [
  { id:'family',   icon:' ', title:'Family at Home',  malayalam:'വീട്ടിൽ',       desc:'Talk with parents, grandparents' },
  { id:'market',   icon:' ', title:'At the Market',   malayalam:'ചന്തയിൽ',      desc:'Shopping in Kerala'             },
  { id:'travel',   icon:' ', title:'Visiting Kerala', malayalam:'കേരളത്തിൽ',    desc:'Travel and social situations'   },
  { id:'children', icon:' ', title:'Kids Corner',     malayalam:'കുട്ടികൾക്ക്', desc:'Fun lessons for NRI children'   },
]

export default function HomeScreen() {
  const navigate = useNavigate()
  return (
    <div className="screen">
      <div className="screen-header">
        <h1>Neela Mozhi</h1>
        <div className="malayalam-title malayalam">നീല മൊഴി</div>
        <p>Speak Malayalam Confidently</p>
      </div>
      <h2 style={{margin:'20px 0 10px', fontSize:'1.1rem', color:'#444'}}>Choose a Scenario</h2>
      {scenarios.map(s => (
        <div
          key={s.id}
          className="card"
          onClick={() => navigate('/conversation', { state: { scenario: s } })}
          style={{display:'flex', alignItems:'center', gap:'16px', cursor:'pointer'}}
        >
          <span style={{fontSize:'2rem'}}>{s.icon}</span>
          <div>
            <strong>{s.title}</strong>
            <div className="malayalam" style={{color:'#f4a261', fontSize:'1rem', marginTop:'2px'}}>
              {s.malayalam}
            </div>
            <div style={{color:'#888', fontSize:'0.85rem', marginTop:'2px'}}>{s.desc}</div>
          </div>
        </div>
      ))}
      <div style={{display:'flex', gap:'12px', marginTop:'20px'}}>
        <button className="btn-primary" onClick={() => navigate('/writing-lab')}
          style={{flex:1}}>  Uncle B's Writing Lab</button>
        <button className="btn-accent" onClick={() => navigate('/sounds')}
          style={{flex:1}}>  Sounds</button>
      </div>
    </div>
  )
}

// src/screens/ConversationScreen.js

import React, { useState, useRef, useEffect } from 'react'
import { useNavigate, useLocation } from 'react-router-dom'

const quickPhrases = [
  'Hello / നമസ്കാരം',
  'How are you? / സുഖമാണോ?',
  'Thank you / നന്ദി',
  "I don't understand / മനസ്സിലായില്ല",
  'What is this? / ഇത് എന്താണ്?',
  'Please speak slowly / പതുക്കെ പറയൂ',
]

export default function ConversationScreen() {
  const navigate = useNavigate()
  const location = useLocation()
  const scenario = location.state?.scenario || { title:'General Practice', malayalam:'പൊതുവേ' }
  const [messages, setMessages] = useState([{
    role:'assistant',
    text:`Hello! I'm Uncle B   Let's practice Malayalam!\nScenario: ${scenario.title}\n\nTap a phrase or type your own!`
  }])
  const [input, setInput] = useState('')
  const [loading, setLoading] = useState(false)
  const bottomRef = useRef(null)

  useEffect(() => {
    bottomRef.current?.scrollIntoView({ behavior:'smooth' })
  }, [messages])

  function sendMessage(text) {
    if (!text.trim()) return
    setMessages(prev => [...prev, { role:'user', text }])
    setInput('')
    setLoading(true)
    setTimeout(() => {
      setMessages(prev => [...prev, {
        role:'assistant',
        text:`Great try!  \n[AI response will appear here once the API is connected]\n\nPractice tip: Say it slowly first, then build up speed!`
      }])
      setLoading(false)
    }, 800)
  }

  return (
    <div style={{display:'flex', flexDirection:'column', height:'100vh'}}>
      <div style={{
        background:'#1a3c5e', color:'white', padding:'16px 20px',
        display:'flex', alignItems:'center', gap:'12px', flexShrink:0
      }}>
        <button onClick={() => navigate('/')}
          style={{background:'none', border:'none', color:'white', fontSize:'1.3rem', cursor:'pointer'}}>
          ←
        </button>
        <div>
          <div style={{fontWeight:700, fontSize:'1rem'}}>{scenario.title}</div>
          <div className="malayalam" style={{color:'#f4a261', fontSize:'0.88rem'}}>{scenario.malayalam}</div>
        </div>
      </div>

      <div style={{flex:1, overflowY:'auto', padding:'16px', display:'flex', flexDirection:'column', gap:'12px'}}>
        {messages.map((msg, i) => (
          <div key={i} style={{display:'flex', justifyContent: msg.role==='user' ? 'flex-end' : 'flex-start'}}>
            <div style={{
              borderRadius:'18px', padding:'12px 16px', maxWidth:'82%',
              lineHeight:1.6, whiteSpace:'pre-line', fontSize:'0.95rem',
              background: msg.role==='user' ? '#1a3c5e' : '#f0f4f8',
              color: msg.role==='user' ? 'white' : '#1a3c5e',
              borderBottomRightRadius: msg.role==='user' ? '4px' : '18px',
              borderBottomLeftRadius: msg.role==='assistant' ? '4px' : '18px',
            }}>
              {msg.role==='assistant' && '  '}{msg.text}
            </div>
          </div>
        ))}
        {loading && <div style={{textAlign:'center', color:'#aaa', fontStyle:'italic', fontSize:'0.88rem'}}>Uncle B is thinking...</div>}
        <div ref={bottomRef} />
      </div>

      <div style={{padding:'10px 14px 20px', background:'#f8f8f8', borderTop:'1px solid #eee', flexShrink:0}}>
        <div style={{display:'flex', gap:'8px', overflowX:'auto', marginBottom:'10px', paddingBottom:'4px'}}>
          {quickPhrases.map(p => (
            <button key={p} onClick={() => sendMessage(p)} style={{
              whiteSpace:'nowrap', background:'#e8f4fd', border:'1px solid #1a3c5e',
              borderRadius:'20px', padding:'6px 14px', cursor:'pointer',
              fontSize:'0.8rem', color:'#1a3c5e'
            }}>{p}</button>
          ))}
        </div>
        <div style={{display:'flex', gap:'8px'}}>
          <input
            value={input}
            onChange={e => setInput(e.target.value)}
            onKeyDown={e => e.key==='Enter' && sendMessage(input)}
            placeholder="Type in English or Malayalam..."
            style={{
              flex:1, padding:'12px 18px', borderRadius:'26px',
              border:'2px solid #1a3c5e', fontSize:'0.95rem', outline:'none'
            }}
          />
          <button onClick={() => sendMessage(input)} style={{
            background:'#1a3c5e', color:'white', border:'none',
            borderRadius:'50%', width:'48px', height:'48px',
            fontSize:'1.1rem', cursor:'pointer'
          }}>➤</button>
        </div>
      </div>
    </div>
  )
}
// src/screens/WritingLabScreen.js
import React, { useState } from 'react'

const phases = [
  {
    phase:1, title:"Uncle B's Ra Family — The Base Shapes",
    letters:[
      { letter:'ര', romanized:'ra',  mnemonic:'The base shape — like a curved arm',       tip:'Soft flap of tongue. Like a quick D sound.' },
      { letter:'റ', romanized:'ṟa',  mnemonic:'Elephant trunk curling above the ra',       tip:'Hard tapped R — tongue hits roof of mouth firmly.' },
      { letter:'ന', romanized:'na',  mnemonic:'Two humps — like a double ra',              tip:'Dental N — tongue touches back of upper front teeth.' },
      { letter:'ല', romanized:'la',  mnemonic:'Ra shape with a tucked-in tail',            tip:'Dental L — tip of tongue behind upper teeth.' },
    ]
  },
  {
    phase:2, title:'Common Consonants',
    letters:[
      { letter:'ക', romanized:'ka',  mnemonic:'Seatbelt — ra with a crossover loop',      tip:'Unaspirated K. Like "k" in "skip" — no puff of air.' },
      { letter:'മ', romanized:'ma',  mnemonic:'Two bumps sitting on a baseline',           tip:'Simple M — same as English.' },
      { letter:'പ', romanized:'pa',  mnemonic:'Flag on a pole',                            tip:'Unaspirated P. Like "p" in "span".' },
      { letter:'വ', romanized:'va',  mnemonic:'A crown with two points',                   tip:'Like English V or W depending on context.' },
    ]
  },
  {
    phase:3, title:'Sibilants & Fricatives',
    letters:[
      { letter:'ശ', romanized:'sha', mnemonic:'Palatal Sh — like a curled shell',          tip:'Like "sh" in shoe. Common and easy for English speakers.' },
      { letter:'ഷ', romanized:'ṣha', mnemonic:'Retroflex Sh — thicker shell shape',       tip:'Stronger Sh — tongue curled further back.' },
      { letter:'സ', romanized:'sa',  mnemonic:'The snake curve',                           tip:'Like "s" in sun. Dental sibilant.' },
      { letter:'ഹ', romanized:'ha',  mnemonic:'Two columns joined at top',                 tip:'Like English H. Breathy, from the throat.' },
    ]
  },
  {
    phase:4, title:'Advanced — Retroflex Letters',
    letters:[
      { letter:'ണ', romanized:'ṇa',  mnemonic:'Harder N — triple hump',                   tip:'Retroflex N — tongue curls back to roof of mouth.' },
      { letter:'ള', romanized:'ḷa',  mnemonic:'Harder L — with a curl underneath',        tip:'Retroflex L — tongue curls toward hard palate.' },
      { letter:'ഴ', romanized:'zha', mnemonic:'Signature Malayalam — the unique curve',   tip:'Unique to Malayalam! Curl tongue back and let it vibrate. The pride of Malayalam!' },
      { letter:'ട', romanized:'ṭa',  mnemonic:'Umbrella with a handle',                   tip:'Retroflex T — tongue curls back then snaps forward.' },
    ]
  },
]

export default function WritingLabScreen() {
  const [activePhase, setActivePhase] = useState(0)
  const [activeLetter, setActiveLetter] = useState(null)

  return (
    <div className="screen">
      <div className="screen-header">
        <h1>Uncle B's Writing Lab</h1>
        <div className="malayalam-title malayalam">എഴുത്ത് ലാബ്</div>
      </div>

      <div className="card" style={{background:'#fff3e0', border:'2px solid #f4a261'}}>
        <div style={{display:'flex', alignItems:'flex-start', gap:'14px'}}>
          <span className="malayalam" style={{fontSize:'2.8rem', color:'#1a3c5e', minWidth:'52px', textAlign:'center'}}>്</span>
          <div>
            <strong>Chandrakkala — <span className="malayalam">ചന്ദ്രക്കല</span></strong>
            <p style={{color:'#555', fontSize:'0.88rem', marginTop:'5px', lineHeight:1.5}}>
              The <em>"a killer"</em> — removes the default vowel sound from a consonant.
            </p>
            <div style={{fontFamily:'monospace', background:'white', padding:'4px 10px', borderRadius:'6px', marginTop:'7px', fontSize:'0.88rem', display:'inline-block'}}>
              ക = ka → ക് = k (no vowel!)
            </div>
            <div style={{color:'#f4a261', marginTop:'6px', fontSize:'0.85rem'}}>
                Think of it as a mute button for the "a" sound.
            </div>
          </div>
        </div>
      </div>

      <div style={{display:'flex', gap:'8px', margin:'18px 0 4px', flexWrap:'wrap'}}>
        {phases.map((p,i) => (
          <button key={i}
            onClick={() => { setActivePhase(i); setActiveLetter(null) }}
            style={{
              flex:1, minWidth:'70px', padding:'10px 4px', borderRadius:'10px',
              border:'2px solid #1a3c5e', cursor:'pointer', fontWeight:600, fontSize:'0.88rem',
              background: activePhase===i ? '#1a3c5e' : 'white',
              color: activePhase===i ? 'white' : '#1a3c5e',
            }}>
            Phase {p.phase}
          </button>
        ))}
      </div>

      <h3 style={{margin:'14px 0 12px', fontSize:'1rem', color:'#444'}}>{phases[activePhase].title}</h3>

      <div style={{display:'grid', gridTemplateColumns:'1fr 1fr', gap:'12px'}}>
        {phases[activePhase].letters.map((letter,i) => (
          <div key={i} className="card"
            onClick={() => setActiveLetter(activeLetter===i ? null : i)}
            style={{textAlign:'center', cursor:'pointer', borderColor: activeLetter===i ? '#f4a261' : 'transparent'}}>
            <div className="malayalam" style={{fontSize:'3rem', color:'#1a3c5e', lineHeight:1.2}}>{letter.letter}</div>
            <div style={{fontWeight:700, marginTop:'4px', color:'#1a3c5e'}}>{letter.romanized}</div>
            <div style={{color:'#888', fontSize:'0.78rem', marginTop:'5px', lineHeight:1.4}}>{letter.mnemonic}</div>
            {activeLetter===i && (
              <div style={{marginTop:'10px', padding:'9px', background:'#e8f4fd', borderRadius:'9px', fontSize:'0.82rem', color:'#1a3c5e', lineHeight:1.5, textAlign:'left'}}>
                  {letter.tip}
              </div>
            )}
          </div>
        ))}
      </div>
    </div>
  )
}

// src/screens/SoundsScreen.js
import React, { useState } from 'react'

const soundsData = [
  { letter:'ഴ', romanized:'zha', difficulty:'★★★', example:'കഴിഞ്ഞു (kazhinju) — finished',   tip:'Completely unique to Malayalam. No equivalent in Hindi, Tamil, or English. Curl tongue back and let it vibrate against the palate.' },
  { letter:'ര', romanized:'ra',  difficulty:'★★',  example:'വരൂ (varoo) — come',               tip:'Soft alveolar flap — like a very quick D. Tongue lightly taps the ridge behind upper teeth once.' },
  { letter:'റ', romanized:'ṟa',  difficulty:'★★',  example:'അറ (ara) — room',                  tip:'Hard tapped R — stronger than ര. Tongue hits roof of mouth firmly. Practice them side by side.' },
  { letter:'ല', romanized:'la',  difficulty:'★',   example:'ലോകം (lokam) — world',              tip:'Dental L — tip of tongue touches back of upper front teeth. Softer than English L.' },
  { letter:'ള', romanized:'ḷa',  difficulty:'★★★', example:'കള (kala) — art / weeds',           tip:'Retroflex L — tongue curls back toward hard palate. Very distinct from dental ല.' },
  { letter:'ണ', romanized:'ṇa',  difficulty:'★★',  example:'പണം (panam) — money',               tip:'Retroflex N — tongue curls back to roof of mouth. Deeper than dental ന.' },
  { letter:'ശ', romanized:'sha', difficulty:'★',   example:'ശരി (shari) — correct / okay',      tip:'Palatal Sh — like "sh" in shoe. Very common and easy for English speakers.' },
  { letter:'ഷ', romanized:'ṣha', difficulty:'★★',  example:'ഷർട്ട് (shirt) — shirt',           tip:'Retroflex Sh — tongue curls back further. Common in Sanskrit-origin words.' },
  { letter:'ന', romanized:'na',  difficulty:'★',   example:'നന്ദി (nandi) — thank you',         tip:'Dental N — tongue touches back of upper front teeth. Softer than English N.' },
  { letter:'ക', romanized:'ka',  difficulty:'★',   example:'കേരളം (keralam) — Kerala',          tip:'Unaspirated K — like "k" in "skip", not "kit". No puff of air after it.' },
]

export default function SoundsScreen() {
  const [active, setActive] = useState(null)

  return (
    <div className="screen">
      <div className="screen-header">
        <h1>Sounds Guide</h1>
        <div className="malayalam-title malayalam">ഉച്ചാരണം</div>
        <p>Tap a letter to see pronunciation tips</p>
      </div>
      {soundsData.map((s,i) => (
        <div key={i} className="card"
          onClick={() => setActive(active===i ? null : i)}
          style={{cursor:'pointer', borderColor: active===i ? '#f4a261' : 'transparent'}}>
          <div style={{display:'flex', alignItems:'center', gap:'16px'}}>
            <div className="malayalam" style={{fontSize:'2.8rem', color:'#1a3c5e', minWidth:'54px', textAlign:'center'}}>{s.letter}</div>
            <div style={{flex:1}}>
              <div style={{display:'flex', justifyContent:'space-between', alignItems:'center'}}>
                <strong style={{fontSize:'1.1rem', color:'#1a3c5e'}}>{s.romanized}</strong>
                <span style={{color:'#f4a261', fontSize:'1rem', letterSpacing:'2px'}}>{s.difficulty}</span>
              </div>
              <div style={{color:'#888', fontSize:'0.84rem', marginTop:'3px'}}>{s.example}</div>
            </div>
          </div>
          {active===i && (
            <div style={{marginTop:'13px', padding:'12px', background:'#e8f4fd', borderRadius:'10px', color:'#1a3c5e', lineHeight:1.65, fontSize:'0.88rem'}}>
                {s.tip}
            </div>
          )}
        </div>
      ))}
    </div>
  )
}

// src/screens/SettingsScreen.js
import React, { useState, useEffect } from 'react'
import { supabase } from '../supabaseClient'

export default function SettingsScreen() {
  const [user, setUser] = useState(null)
  const [showDeleteConfirm, setShowDeleteConfirm] = useState(false)
  const [deleting, setDeleting] = useState(false)

  useEffect(() => {
    supabase.auth.getSession().then(({ data: { session } }) => {
      setUser(session?.user ?? null)
    })
  }, [])

  async function handleSignOut() {
    await supabase.auth.signOut()
    window.location.href = '/login'
  }

  async function handleDeleteAccount() {
    setDeleting(true)
    try {
      const { error } = await supabase.functions.invoke('delete-user', {
        body: { user_id: user.id }
      })
      if (error) throw error
      await supabase.auth.signOut()
      window.location.href = '/login'
    } catch {
      alert('Error deleting account. Please contact support.')
      setDeleting(false)
    }
  }

  return (
    <div className="screen">
      <div className="screen-header">
        <h1>Settings</h1>
        <div className="malayalam-title malayalam">ക്രമീകരണം</div>
      </div>

      <div className="card">
        <p style={{color:'#888', fontSize:'0.85rem'}}>Signed in as</p>
        <p style={{fontWeight:700, marginTop:'4px', color:'#1a3c5e', wordBreak:'break-all'}}>{user?.email}</p>
      </div>

      <div className="card">
        <h3 style={{marginBottom:'8px', color:'#1a3c5e'}}>Privacy Policy</h3>
        <a href="https://neela-malayalam.vercel.app/privacy" target="_blank" rel="noreferrer"
          style={{color:'#1a3c5e', textDecoration:'underline', fontSize:'0.95rem'}}>
          View Privacy Policy ↗
        </a>
      </div>

      <div className="card" style={{background:'#fff8f0'}}>
        <h3 style={{marginBottom:'8px', color:'#1a3c5e'}}>  AI Disclosure</h3>
        <p style={{color:'#555', fontSize:'0.88rem', lineHeight:1.65}}>
          This app uses AI to help you practice Malayalam. Your messages may be processed
          by our AI provider to generate responses. We do not store conversation content.
        </p>
      </div>

      <button className="btn-primary" onClick={handleSignOut} style={{marginTop:'16px'}}>
        Sign Out
      </button>

      {!showDeleteConfirm ? (
        <button onClick={() => setShowDeleteConfirm(true)} style={{
          width:'100%', marginTop:'12px', padding:'14px',
          background:'none', border:'2px solid #e74c3c',
          color:'#e74c3c', borderRadius:'12px', fontSize:'1rem',
          cursor:'pointer', fontWeight:600
        }}>
          Delete My Account
        </button>
      ) : (
        <div className="card" style={{border:'2px solid #e74c3c', marginTop:'12px'}}>
          <p style={{color:'#e74c3c', fontWeight:700, marginBottom:'8px'}}>  Are you sure?</p>
          <p style={{color:'#666', fontSize:'0.85rem', marginBottom:'16px', lineHeight:1.6}}>
            This permanently deletes your account and all learning data. This cannot be undone.
          </p>
          <button onClick={handleDeleteAccount} disabled={deleting} style={{
            width:'100%', padding:'14px', background:'#e74c3c', color:'white',
            border:'none', borderRadius:'10px', fontSize:'1rem',
            cursor:'pointer', marginBottom:'8px', fontWeight:600,
            opacity: deleting ? 0.5 : 1
          }}>
            {deleting ? 'Deleting...' : 'Yes, Delete My Account'}
          </button>
          <button onClick={() => setShowDeleteConfirm(false)} style={{
            width:'100%', padding:'14px', background:'#eee',
            border:'none', borderRadius:'10px', fontSize:'1rem', cursor:'pointer'
          }}>
            Cancel
          </button>
        </div>
      )}
    </div>
  )
}

