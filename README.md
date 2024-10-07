import React, { useState } from 'react';
import { motion } from 'framer-motion';

const messages = [
  'Message 1: Your Next.js site has deployed!',
  'Message 2: New comment on your blog post!',
  'Message 3: A new issue was opened on your repository!',
];

export default function Home() {
  const [inboxMessages, setInboxMessages] = useState([]);

  const handleAddMessage = () => {
    if (inboxMessages.length < messages.length) {
      setInboxMessages([...inboxMessages, messages[inboxMessages.length]]);
    }
  };

  return (
    <div className="container">
      <h1>Next.js Inbox</h1>
      <div className="inbox">
        {inboxMessages.map((msg, idx) => (
          <motion.div
            key={idx}
            className="message"
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.5 }}
          >
            {msg}
          </motion.div>
        ))}
      </div>
      <button onClick={handleAddMessage}>Add Message</button>
    </div>
  );
}
